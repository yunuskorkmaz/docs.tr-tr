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
# <a name="treenodecollectionitem-throws-exception-if-node-is-assigned-elsewhere"></a><span data-ttu-id="4d13e-103">TreeNodeCollection. Item, düğüm başka bir yere atanırsa özel durum oluşturur</span><span class="sxs-lookup"><span data-stu-id="4d13e-103">TreeNodeCollection.Item throws exception if node is assigned elsewhere</span></span>

<span data-ttu-id="4d13e-104"><xref:System.Windows.Forms.TreeNodeCollection.Item(System.Int32)?displayProperty=nameWithType><xref:System.ArgumentException>atanmakta olan düğüm zaten başka bir <xref:System.Windows.Forms.TreeView> dizinde veya bu dizine zaten bağlıysa, bir oluşturur <xref:System.Windows.Forms.TreeView> .</span><span class="sxs-lookup"><span data-stu-id="4d13e-104"><xref:System.Windows.Forms.TreeNodeCollection.Item(System.Int32)?displayProperty=nameWithType> throws an <xref:System.ArgumentException> if the node being assigned is already bound to another <xref:System.Windows.Forms.TreeView> or to this <xref:System.Windows.Forms.TreeView> at a different index.</span></span>

## <a name="change-description"></a><span data-ttu-id="4d13e-105">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="4d13e-105">Change description</span></span>

<span data-ttu-id="4d13e-106">Önceki .NET sürümlerinde, bir koleksiyona zaten bir bağlansa bile bir ağaç düğümü atayabilirsiniz <xref:System.Windows.Forms.TreeView> .</span><span class="sxs-lookup"><span data-stu-id="4d13e-106">In previous .NET versions, you can assign a tree node to a collection even if it's already bound to a <xref:System.Windows.Forms.TreeView>.</span></span> <span data-ttu-id="4d13e-107">Bu, yinelenen düğümlere yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="4d13e-107">This can lead to duplicated nodes.</span></span> <span data-ttu-id="4d13e-108">.NET 6 ' dan itibaren, <xref:System.Windows.Forms.TreeNodeCollection.Item(System.Int32)?displayProperty=nameWithType> <xref:System.ArgumentException> atanmakta olan düğüm zaten başka bir <xref:System.Windows.Forms.TreeView> dizinde veya bu dizine zaten bağlıysa, bir oluşturur <xref:System.Windows.Forms.TreeView> .</span><span class="sxs-lookup"><span data-stu-id="4d13e-108">Starting in .NET 6, <xref:System.Windows.Forms.TreeNodeCollection.Item(System.Int32)?displayProperty=nameWithType> throws an <xref:System.ArgumentException> if the node being assigned is already bound to another <xref:System.Windows.Forms.TreeView> or to this <xref:System.Windows.Forms.TreeView> at a different index.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="4d13e-109">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="4d13e-109">Reason for change</span></span>

<span data-ttu-id="4d13e-110">Giriş parametresinin doğrulanması, diğer API 'lerin davranışıyla tutarlıdır `TreeNodeCollection` .</span><span class="sxs-lookup"><span data-stu-id="4d13e-110">Validating the input parameter is consistent with the behavior of other `TreeNodeCollection` APIs.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="4d13e-111">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="4d13e-111">Version introduced</span></span>

<span data-ttu-id="4d13e-112">.NET 6 Preview 1</span><span class="sxs-lookup"><span data-stu-id="4d13e-112">.NET 6 Preview 1</span></span>

## <a name="recommended-action"></a><span data-ttu-id="4d13e-113">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="4d13e-113">Recommended action</span></span>

<span data-ttu-id="4d13e-114">Koleksiyona atamadan önce bir bağlantısını kesin olarak yaptığınızdan emin olun `TreeNode` .</span><span class="sxs-lookup"><span data-stu-id="4d13e-114">Make sure to unbind a `TreeNode` before assigning it to the collection.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="4d13e-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="4d13e-115">Affected APIs</span></span>

<xref:System.Windows.Forms.TreeNodeCollection.Item(System.Int32)?displayProperty=fullName>

<!--

### Affected APIs

- `P:System.Windows.Forms.TreeNodeCollection.Item(System.Int32)`

### Category

Windows Forms

-->
