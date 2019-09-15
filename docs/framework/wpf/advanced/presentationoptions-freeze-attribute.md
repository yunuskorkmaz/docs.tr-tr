---
title: PresentationOptions:Freeze Özniteliği
ms.date: 03/30/2017
helpviewer_keywords:
- Freeze attribute [WPF]
- Freezable elements [WPF]
- PresentationOptions prefix [WPF]
ms.assetid: 391032dd-2fba-4804-bb8a-3b071797a9f4
ms.openlocfilehash: d3e0cee293a9585b972b0145da953976ed94b74c
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991423"
---
# <a name="presentationoptionsfreeze-attribute"></a><span data-ttu-id="9cb9d-102">PresentationOptions:Freeze Özniteliği</span><span class="sxs-lookup"><span data-stu-id="9cb9d-102">PresentationOptions:Freeze Attribute</span></span>
<span data-ttu-id="9cb9d-103"><xref:System.Windows.Freezable.IsFrozen%2A> Durumu `true` kapsayan öğe<xref:System.Windows.Freezable> üzerinde olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="9cb9d-103">Sets the <xref:System.Windows.Freezable.IsFrozen%2A> state to `true` on the containing <xref:System.Windows.Freezable> element.</span></span> <span data-ttu-id="9cb9d-104">Belirtilen <xref:System.Windows.Freezable> özniteliğiolmadan`PresentationOptions:Freeze` bir için varsayılan davranış, yükleme zamanında ve çalışma zamanında genel <xref:System.Windows.Freezable> davranışa bağımlıdır. <xref:System.Windows.Freezable.IsFrozen%2A> `false`</span><span class="sxs-lookup"><span data-stu-id="9cb9d-104">Default behavior for a <xref:System.Windows.Freezable> without the `PresentationOptions:Freeze` attribute specified is that <xref:System.Windows.Freezable.IsFrozen%2A> is `false` at load time, and dependent on general <xref:System.Windows.Freezable> behavior at runtime.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="9cb9d-105">XAML Öznitelik Kullanımı</span><span class="sxs-lookup"><span data-stu-id="9cb9d-105">XAML Attribute Usage</span></span>  
  
```xaml  
<object  
  xmlns:PresentationOptions="http://schemas.microsoft.com/winfx/2006/xaml/presentation/options"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="PresentationOptions">  
    <freezableElement PresentationOptions:Freeze="true"/>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="9cb9d-106">XAML Değerleri</span><span class="sxs-lookup"><span data-stu-id="9cb9d-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`PresentationOptions`|<span data-ttu-id="9cb9d-107">XML 1,0 belirtimine göre geçerli herhangi bir ön ek dizesi olabilen bir XML ad alanı öneki.</span><span class="sxs-lookup"><span data-stu-id="9cb9d-107">An XML namespace prefix, which can be any valid prefix string, per the XML 1.0 specification.</span></span> <span data-ttu-id="9cb9d-108">Bu belgede `PresentationOptions` tanımlama amacıyla ön ek kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9cb9d-108">The prefix `PresentationOptions` is used for identification purposes in this documentation.</span></span>|  
|`freezableElement`|<span data-ttu-id="9cb9d-109">Türetilmiş herhangi bir sınıfını <xref:System.Windows.Freezable>örnekleyen öğe.</span><span class="sxs-lookup"><span data-stu-id="9cb9d-109">An element that instantiates any derived class of <xref:System.Windows.Freezable>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9cb9d-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9cb9d-110">Remarks</span></span>  
 <span data-ttu-id="9cb9d-111">Özniteliği, `http://schemas.microsoft.com/winfx/2006/xaml/presentation/options` XML ad alanında tanımlanmış tek öznitelik veya diğer programlama öğesidir. `Freeze`</span><span class="sxs-lookup"><span data-stu-id="9cb9d-111">The `Freeze` attribute is the only attribute or other programming element defined in the `http://schemas.microsoft.com/winfx/2006/xaml/presentation/options` XML namespace.</span></span> <span data-ttu-id="9cb9d-112">Özniteliği `Freeze` , bu özel ad alanında özellikle, kök öğe bildirimlerinin bir parçası olarak, [mc: Ignorable özniteliği](mc-ignorable-attribute.md) kullanılarak, yoksayılabilir olarak atanabilmesi için vardır.</span><span class="sxs-lookup"><span data-stu-id="9cb9d-112">The `Freeze` attribute exists in this special namespace specifically so that it can be designated as ignorable, using [mc:Ignorable Attribute](mc-ignorable-attribute.md) as part of the root element declarations.</span></span> <span data-ttu-id="9cb9d-113">Tüm `Freeze` <xref:System.Windows.Freezable> [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemci uygulamalarının yükleme süresini donduramadığı, ancak bu özellik, belirtiminin bir parçası olmadığı için, yoksayılabilir olması gereken neden olur. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9cb9d-113">The reason that `Freeze` must be able to be ignorable is because not all [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor implementations are able to freeze a <xref:System.Windows.Freezable> at load time; this capability is not part of the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] specification.</span></span>  
  
 <span data-ttu-id="9cb9d-114">`Freeze` Özniteliği işleyebilme özelliği, derlenmiş uygulamalar [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] için işlenen [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemcide özellikle de yerleşiktir.</span><span class="sxs-lookup"><span data-stu-id="9cb9d-114">The ability to process the `Freeze` attribute is specifically built in to the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor that processes [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] for compiled applications.</span></span> <span data-ttu-id="9cb9d-115">Özniteliği hiçbir sınıf tarafından desteklenmez ve öznitelik sözdizimi genişletilebilir veya değiştirilebilir değildir.</span><span class="sxs-lookup"><span data-stu-id="9cb9d-115">The attribute is not supported by any class, and the attribute syntax is not extensible or modifiable.</span></span> <span data-ttu-id="9cb9d-116">Kendi [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemcinizi uygulamadıysanız, yükleme zamanında <xref:System.Windows.Freezable> öğelerde `Freeze` özniteliği işlerken, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemcinin donduruyor davranışını [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] paralel olarak seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9cb9d-116">If you are implementing your own [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor you can choose to parallel the freezing behavior of the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor when processing the `Freeze` attribute on <xref:System.Windows.Freezable> elements at load time.</span></span>  
  
 <span data-ttu-id="9cb9d-117">(Büyük/küçük `Freeze` harfe duyarlı değil) dışındaki öznitelik için herhangi bir değer bir yükleme zamanı hatası oluşturur. `true`</span><span class="sxs-lookup"><span data-stu-id="9cb9d-117">Any value for the `Freeze` attribute other than `true` (not case sensitive) generates a load time error.</span></span> <span data-ttu-id="9cb9d-118">`Freeze` ( `false` Özniteliği bir hata değil, ancak zaten varsayılan değer, bu nedenle hiçbir şey yapmaz). `false`</span><span class="sxs-lookup"><span data-stu-id="9cb9d-118">(Specifying the `Freeze` attribute as `false` is not an error, but that is already the default, so setting to `false` does nothing).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cb9d-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9cb9d-119">See also</span></span>

- <xref:System.Windows.Freezable>
- [<span data-ttu-id="9cb9d-120">Freezable Nesnelerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="9cb9d-120">Freezable Objects Overview</span></span>](freezable-objects-overview.md)
- [<span data-ttu-id="9cb9d-121">mc:Ignorable Özniteliği</span><span class="sxs-lookup"><span data-stu-id="9cb9d-121">mc:Ignorable Attribute</span></span>](mc-ignorable-attribute.md)
