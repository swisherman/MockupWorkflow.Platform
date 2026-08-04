# Photoshop Templates

This directory contains the reusable Photoshop templates used by the Mockup Workflow platform.

## Organization

Each product type has its own folder.

Example:

templates/
├── printable-wall-art/
├── tshirt/
├── mug/

## Master Template

Each product type contains one master template.

Example:

printable-wall-art-master.psd

The master is the authoritative source for:

- Layer structure
- Smart Objects
- Layer names
- Effects
- Automation compatibility

Changes should always be made to the master first.

## Variations

Additional PSDs are derived from the master.

Examples:

- printable-wall-art-scandinavian.psd
- printable-wall-art-cottage.psd
- printable-wall-art-office.psd

Derived templates should preserve the required automation layer names.

## Required Layer Names

The Photoshop automation expects these layers to exist.

- FRAME
- MAT
- ARTWORK
- WALL

Do not rename these layers without updating the automation.

## Goal

Templates provide reusable presentation styles while allowing the Photoshop UXP automation to generate marketplace-ready mockups from the same artwork.