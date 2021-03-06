---
title: 'Son değişiklik: TreeNodeCollection. Item (Int32), kullanımda olan düğüm için ArgumentException oluşturur'
description: Atanmakta olan düğüm zaten bir TreeView 'a atanmışsa, .NET 6 ' daki Son değişiklik hakkında bilgi edinin.
ms.date: 01/19/2021
ms.openlocfilehash: 29727da2e4bc3d6ac89ed88819bf03d058603f77
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102255704"
---
# <a name="treenodecollectionitem-throws-exception-if-node-is-assigned-elsewhere"></a>TreeNodeCollection. Item, düğüm başka bir yere atanırsa özel durum oluşturur

<xref:System.Windows.Forms.TreeNodeCollection.Item(System.Int32)?displayProperty=nameWithType><xref:System.ArgumentException>atanmakta olan düğüm zaten başka bir <xref:System.Windows.Forms.TreeView> dizinde veya bu dizine zaten bağlıysa, bir oluşturur <xref:System.Windows.Forms.TreeView> .

## <a name="change-description"></a>Açıklamayı Değiştir

Önceki .NET sürümlerinde, bir koleksiyona zaten bir bağlansa bile bir ağaç düğümü atayabilirsiniz <xref:System.Windows.Forms.TreeView> . Bu, yinelenen düğümlere yol açabilir. .NET 6 ' dan itibaren, <xref:System.Windows.Forms.TreeNodeCollection.Item(System.Int32)?displayProperty=nameWithType> <xref:System.ArgumentException> atanmakta olan düğüm zaten başka bir <xref:System.Windows.Forms.TreeView> dizinde veya bu dizine zaten bağlıysa, bir oluşturur <xref:System.Windows.Forms.TreeView> .

## <a name="reason-for-change"></a>Değişiklik nedeni

Giriş parametresinin doğrulanması, diğer API 'lerin davranışıyla tutarlıdır `TreeNodeCollection` .

## <a name="version-introduced"></a>Sunulan sürüm

.NET 6 Preview 1

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
