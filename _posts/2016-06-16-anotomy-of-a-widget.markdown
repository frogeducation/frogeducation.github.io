---
layout: post
title:  "Anatomy of a Frog Widget"
date:   2016-06-16 10:00:00 +0100
categories: widget architecture
---

Widgets, by design, are simplified Applications intended to run within a Site. Inheriting from the same base class - Frog.Controller - therefore having access to the same static and prototype methods as Applications, Widgets can be as simple or complex as they need to be (although they tend to err on the simple side).

It is common for an Application to have a companion Widget, such as the Calendar Application and the Calendar Widget. This provides the User with a "quick look" into their Application data without having to physically launch said Application, and also allows the sharing of data to Users who may have access to the companion Widget but not the Application.

The key difference between Widgets and Applications are:

 * Widget State
 * Widget Preferences

## Widget State

During their lifecycle, Widgets can go be in one of two distinct states:

 * live - this state is triggered when the Widget is instantiated in the Page of a Site and is the default state
 * edit - this state is triggered when the Sites Editor is enabled (while editing a Site)

This state-based approach is useful for displaying different information to the user when editing a Site:

 * Simplify the Widget display for easier drag-drop interaction; as Widget Preferences are rendered in the Sites Editor and not the Site itself, it is (usually) unnecessary to render anything other than a placeholder within the Widget

 * Reduce unnecessary network and processing overhead; again, remove the API calls and processing which is usually associated with a Widget in its live state

## Widget Preferences

Widget preferences present themselves as options to a user when a site is in 'edit' mode.  We have range of options types from simplistic 'text' or 'boolean' options through to 'file_uploads' and 'lists' that integrate much more deeply with our technology.

#### Example prefs

        prefs: {
            "network_path": {
                "type": "networkpath",
                "defaultValue": "|"
            },
            "widget_title": {
                "type": "text",
                "label": "preference.widget_title.label",
                "defaultValue": "preference.widget_title.default_value"
            },
            "show_file_actions": {
                "type": "boolean",
                "label": "preference.show_file_actions.label",
                "defaultValue": true
            },
            "display_list_view": {
                "type": "boolean",
                "label": "preference.display_list_view.label",
                "defaultValue": false
            }
        }

## Styling and Formatting a Widget

We use  html and css render a widget into something useful to the user.  These are included as part of the widget file and reference locations relative to the widget. Generally widgets follow the system level design guide but this methodology allows for localised UI tweaks.

## Example Widget

    steal({ src: '//lib/lib.js', packaged: false, ignore: steal.isRhino }, './public/css/css.js', './widget.ejs').then(function( $ ) {

        /*
         * @class Simple
         * @parent index Widgets
         * @tag widget, simple
         *
         * ###Time Widget
         *
         * Widget provides user abililty to view the browser time
         *
         */
        Frog.Widget.Controller('Widget.Simple', {},
        /* @Prototype*/
        {
            /*
            * The prefs that can be set by the editor user for the time widget
            *
            * @type Object
            */
           prefs: {},

           /**
            * Cache the containing div so no need to do a lookup on every render call
            *
            * @attribute
            */
           container: null,

           /**
            * Start the widget
            *
            * @param {Object} options
            * @return {NULL}
            */
           init: function( options ) {
               this.container = this.element.find('div');
               this.container.html("Hello World");
           }

           /*
             * @trigger widget.edit
             * Adds edit class to widget
             *
             * @param {HTMLElement} el The element received
             * @param {Object} ev The event triggered
             * @return {null}
             */
            'widget.edit': function( el,ev ){
                
            },

            /*
             * @trigger widget.live
             * Removes edit class from widget
             *
             * @param {HTMLElement} el The element received
             * @param {Object} ev The event triggered
             * @return {null}
             */
            'widget.live': function( el,ev ){
                
            }

       });
    });