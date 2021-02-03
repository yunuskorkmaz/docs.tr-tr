---
title: 'Son değişiklik: TreeNodeCollection. Item (Int32), kullanımda olan düğüm için ArgumentException oluşturur'
description: Atanmakta olan düğüm zaten bir TreeView 'a atanmışsa, .NET 6,0 'deki Son değişiklik hakkında bilgi edinin.
ms.date: 01/19/2021
ms.openlocfilehash: efd6ca5d594b2aa64e10cce2cef6c0e1c411bb1e
ms.sourcegitcommit: f2ab02d9a780819ca2e5310bbcf5cfe5b7993041
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2021
ms.locfileid: "99506608"
---
# <a name="treenodecollectionitem-throws-exception-if-node-is-assigned-elsewhere"></a>TreeNodeCollection. Item, düğüm başka bir yere atanırsa özel durum oluşturur

<xref:System.Windows.Forms.TreeNodeCollection.Item(System.Int32)?displayProperty=nameWithType><xref:System.ArgumentException>atanmakta olan düğüm zaten başka bir <xref:System.Windows.Forms.TreeView> dizinde veya bu dizine zaten bağlıysa, bir oluşturur <xref:System.Windows.Forms.TreeView> .

## <a name="change-description"></a>Açıklamayı Değiştir

Önceki .NET sürümlerinde, bir koleksiyona zaten bir bağlansa bile bir ağaç düğümü atayabilirsiniz <xref:System.Windows.Forms.TreeView> . Bu, yinelenen düğümlere yol açabilir. .NET 6,0 ' den başlayarak, <xref:System.Windows.Forms.TreeNodeCollection.Item(System.Int32)?displayProperty=nameWithType> <xref:System.ArgumentException> atanmakta olan düğüm zaten başka bir dizinde diğerine veya başka bir dizine bağlıysa bir oluşturur <xref:System.Windows.Forms.TreeView> <xref:System.Windows.Forms.TreeView> .

## <a name="reason-for-change"></a>Değişiklik nedeni

Giriş parametresinin doğrulanması, diğer API 'lerin davranışıyla tutarlıdır `TreeNodeCollection` .

## <a name="version-introduced"></a>Sunulan sürüm

.NET 6,0 Preview 1

## <a name="recommended-action"></a>Önerilen eylem

Koleksiyona atamadan önce bir bağlantısını kesin olarak yaptığınızdan emin olun `TreeNode` .

## <a name="affected-apis"></a>Etkilenen API’ler

<xref:System.Windows.Forms.TreeNodeCollection.Item(System.Int32)?displayProperty=fullName>

<!--

### Affected APIs

- `P:System.Windows.Forms.TreeNodeCollection.Item(System.Int32)`

### Category

Windows Forms

-->
