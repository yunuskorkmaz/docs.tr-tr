---
title: "PresentationOptions:Freeze Özniteliği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Freeze attribute [WPF]
- Freezable elements [WPF]
- PresentationOptions prefix [WPF]
ms.assetid: 391032dd-2fba-4804-bb8a-3b071797a9f4
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d8f1a876f65941afb159d4c3d8904ab4426d9177
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="presentationoptionsfreeze-attribute"></a><span data-ttu-id="c13aa-102">PresentationOptions:Freeze Özniteliği</span><span class="sxs-lookup"><span data-stu-id="c13aa-102">PresentationOptions:Freeze Attribute</span></span>
<span data-ttu-id="c13aa-103">Ayarlar <xref:System.Windows.Freezable.IsFrozen%2A> durumunu `true` çağırılarak <xref:System.Windows.Freezable> öğesi.</span><span class="sxs-lookup"><span data-stu-id="c13aa-103">Sets the <xref:System.Windows.Freezable.IsFrozen%2A> state to `true` on the containing <xref:System.Windows.Freezable> element.</span></span> <span data-ttu-id="c13aa-104">Varsayılan davranışı bir <xref:System.Windows.Freezable> olmadan `PresentationOptions:Freeze` belirtilen özniteliği olan <xref:System.Windows.Freezable.IsFrozen%2A> olan `false` yükleme süresini ve genel bağımlı <xref:System.Windows.Freezable> çalışma zamanında davranışı.</span><span class="sxs-lookup"><span data-stu-id="c13aa-104">Default behavior for a <xref:System.Windows.Freezable> without the `PresentationOptions:Freeze` attribute specified is that <xref:System.Windows.Freezable.IsFrozen%2A> is `false` at load time, and dependent on general <xref:System.Windows.Freezable> behavior at runtime.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="c13aa-105">XAML Öznitelik Kullanımı</span><span class="sxs-lookup"><span data-stu-id="c13aa-105">XAML Attribute Usage</span></span>  
  
```  
<object  
  xmlns:PresentationOptions="http://schemas.microsoft.com/winfx/2006/xaml/presentation/options"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="PresentationOptions">  
    <freezableElement PresentationOptions:Freeze="true"/>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="c13aa-106">XAML Değerleri</span><span class="sxs-lookup"><span data-stu-id="c13aa-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`PresentationOptions`|<span data-ttu-id="c13aa-107">XML 1.0 belirtimi başına herhangi bir geçerli önek dizesi olabilen bir XML ad alanı öneki.</span><span class="sxs-lookup"><span data-stu-id="c13aa-107">An XML namespace prefix, which can be any valid prefix string, per the XML 1.0 specification.</span></span> <span data-ttu-id="c13aa-108">Önek `PresentationOptions` bu belgede tanımlama amacıyla kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c13aa-108">The prefix `PresentationOptions` is used for identification purposes in this documentation.</span></span>|  
|`freezableElement`|<span data-ttu-id="c13aa-109">Başlatır herhangi bir öğeyi türetilmiş sınıf <xref:System.Windows.Freezable>.</span><span class="sxs-lookup"><span data-stu-id="c13aa-109">An element that instantiates any derived class of <xref:System.Windows.Freezable>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c13aa-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c13aa-110">Remarks</span></span>  
 <span data-ttu-id="c13aa-111">`Freeze` Özniteliktir yalnızca öznitelik veya diğer programlama öğenin tanımlandığı `http://schemas.microsoft.com/winfx/2006/xaml/presentation/options` XML ad alanı.</span><span class="sxs-lookup"><span data-stu-id="c13aa-111">The `Freeze` attribute is the only attribute or other programming element defined in the `http://schemas.microsoft.com/winfx/2006/xaml/presentation/options` XML namespace.</span></span> <span data-ttu-id="c13aa-112">`Freeze` Özniteliği var. Bu özel ad alanında özellikle bu şekilde yoksayılabilir, kullanarak belirlenebilir böylece [mc: yoksayılabilir özniteliği](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md) kök öğesi bildirimlerinin bir parçası olarak.</span><span class="sxs-lookup"><span data-stu-id="c13aa-112">The `Freeze` attribute exists in this special namespace specifically so that it can be designated as ignorable, using [mc:Ignorable Attribute](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md) as part of the root element declarations.</span></span> <span data-ttu-id="c13aa-113">Nedeni, `Freeze` yoksayılabilir kurabilmesi gerekir çünkü tüm değil [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemcisi uygulamaları Dondur mümkün bir <xref:System.Windows.Freezable> yükleme zamanında; bu özelliği değil parçası [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] belirtimi.</span><span class="sxs-lookup"><span data-stu-id="c13aa-113">The reason that `Freeze` must be able to be ignorable is because not all [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor implementations are able to freeze a <xref:System.Windows.Freezable> at load time; this capability is not part of the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] specification.</span></span>  
  
 <span data-ttu-id="c13aa-114">İşleme yeteneği `Freeze` özniteliği özellikle yerleşik için [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işler İşlemci [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] derlenmiş uygulamalar.</span><span class="sxs-lookup"><span data-stu-id="c13aa-114">The ability to process the `Freeze` attribute is specifically built in to the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor that processes [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] for compiled applications.</span></span> <span data-ttu-id="c13aa-115">Öznitelik herhangi bir sınıf tarafından desteklenmiyor ve öznitelik sözdizimi genişletilebilir veya değiştirilebilir değil.</span><span class="sxs-lookup"><span data-stu-id="c13aa-115">The attribute is not supported by any class, and the attribute syntax is not extensible or modifiable.</span></span> <span data-ttu-id="c13aa-116">Kendi uyguluyorsanız, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dondurma davranışına paralel seçebilirsiniz İşlemci [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlerken İşlemci `Freeze` özniteliği <xref:System.Windows.Freezable> yükleme zamanında öğeleri.</span><span class="sxs-lookup"><span data-stu-id="c13aa-116">If you are implementing your own [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor you can choose to parallel the freezing behavior of the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor when processing the `Freeze` attribute on <xref:System.Windows.Freezable> elements at load time.</span></span>  
  
 <span data-ttu-id="c13aa-117">Herhangi bir değer `Freeze` dışında özniteliği `true` (büyük/küçük harfe duyarlı değildir) bir yükleme zamanı hatası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c13aa-117">Any value for the `Freeze` attribute other than `true` (not case sensitive) generates a load time error.</span></span> <span data-ttu-id="c13aa-118">(Belirtme `Freeze` olarak özniteliği `false` bir hata değildir, ancak zaten şekilde ayarlamak varsayılan `false` hiçbir şey yapmaz).</span><span class="sxs-lookup"><span data-stu-id="c13aa-118">(Specifying the `Freeze` attribute as `false` is not an error, but that is already the default, so setting to `false` does nothing).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c13aa-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c13aa-119">See Also</span></span>  
 <xref:System.Windows.Freezable>  
 [<span data-ttu-id="c13aa-120">Freezable nesnelere genel bakış</span><span class="sxs-lookup"><span data-stu-id="c13aa-120">Freezable Objects Overview</span></span>](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [<span data-ttu-id="c13aa-121">mc: yoksayılabilir özniteliği</span><span class="sxs-lookup"><span data-stu-id="c13aa-121">mc:Ignorable Attribute</span></span>](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md)
