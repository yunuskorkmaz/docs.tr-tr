---
title: Özel Denetim Boyama ve İşleme
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], rendering
- custom controls [Windows Forms], painting
- user controls [Windows Forms], painting
ms.assetid: a09dbf76-0966-4cbf-a66a-2083ba98e068
ms.openlocfilehash: 14abac5678bfffa3cdb61307fd3cb54681c82a99
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67506090"
---
# <a name="custom-control-painting-and-rendering"></a><span data-ttu-id="cdd08-102">Özel Denetim Boyama ve İşleme</span><span class="sxs-lookup"><span data-stu-id="cdd08-102">Custom Control Painting and Rendering</span></span>
<span data-ttu-id="cdd08-103">Özel boyama denetimlerin .NET Framework tarafından daha kolay pek çok karmaşık görev biridir.</span><span class="sxs-lookup"><span data-stu-id="cdd08-103">Custom painting of controls is one of the many complicated tasks made easy by the .NET Framework.</span></span> <span data-ttu-id="cdd08-104">Özel denetim yazarken, denetiminizin grafik görünümü ile ilgili birçok seçeneğiniz vardır.</span><span class="sxs-lookup"><span data-stu-id="cdd08-104">When authoring a custom control, you have many options regarding your control's graphical appearance.</span></span> <span data-ttu-id="cdd08-105">Devralınan bir denetim yazıyorsanız `Control`, Denetim, grafik gösterimi işleme veren kod sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="cdd08-105">If you are authoring a control that inherits from the `Control`, you must provide code that allows your control to render its graphical representation.</span></span> <span data-ttu-id="cdd08-106">Devralarak bir kullanıcı denetimi oluşturuyorsanız `UserControl`, veya devraldığını Windows Forms denetimleri birinden, standart grafik gösterimi geçersiz kılabilir ya da kendi grafik kodunu sağlayın.</span><span class="sxs-lookup"><span data-stu-id="cdd08-106">If you are creating a user control by inheriting from the `UserControl`, or are inheriting from one of the Windows Forms controls, you may override the standard graphical representation and provide your own graphics code.</span></span> <span data-ttu-id="cdd08-107">Bağlı denetimler için özel işleme sağlamak istiyorsanız bir `UserControl` geliştirmekte olduğunuz, seçeneklerinizi daha sınırlı olur, ancak yine de çok çeşitli grafik denetimleri ve uygulamaları olasılıklarını izin.</span><span class="sxs-lookup"><span data-stu-id="cdd08-107">If you want to provide custom rendering for the constituent controls of a `UserControl` you are authoring, your options become more limited, but still allow a wide range of graphical possibilities for your controls and applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cdd08-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="cdd08-108">In This Section</span></span>  
 [<span data-ttu-id="cdd08-109">Windows Forms Denetimini İşleme</span><span class="sxs-lookup"><span data-stu-id="cdd08-109">Rendering a Windows Forms Control</span></span>](rendering-a-windows-forms-control.md)  
 <span data-ttu-id="cdd08-110">Bir denetim görüntüler mantığını nasıl programlama yapılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="cdd08-110">Shows how to program the logic that displays a control.</span></span>  
  
 [<span data-ttu-id="cdd08-111">Kullanıcı Çizimli Denetimler</span><span class="sxs-lookup"><span data-stu-id="cdd08-111">User-Drawn Controls</span></span>](user-drawn-controls.md)  
 <span data-ttu-id="cdd08-112">Yazma ve işleme kodunu denetlemek için geçersiz kılma içinde yer alan adımların bir genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="cdd08-112">Gives an overview of the steps involved in writing and overriding rendering code for your control.</span></span>  
  
 [<span data-ttu-id="cdd08-113">Bağlı Denetimler</span><span class="sxs-lookup"><span data-stu-id="cdd08-113">Constituent Controls</span></span>](constituent-controls.md)  
 <span data-ttu-id="cdd08-114">Bağlı denetimler için özel işleme kodu, kullanıcı denetimleri ve forms uygulanacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="cdd08-114">Describes how to implement custom rendering code for constituent controls in your user controls and forms.</span></span>  
  
 [<span data-ttu-id="cdd08-115">Nasıl yapılır: Çalışma zamanında denetiminizi görünmez yapma</span><span class="sxs-lookup"><span data-stu-id="cdd08-115">How to: Make Your Control Invisible at Run Time</span></span>](how-to-make-your-control-invisible-at-run-time.md)  
 <span data-ttu-id="cdd08-116">Nasıl kullanılacağını gösterir <xref:System.Windows.Forms.Control.Visible%2A> özelliğini gizler ve bir denetimi gösterir.</span><span class="sxs-lookup"><span data-stu-id="cdd08-116">Shows how to use the <xref:System.Windows.Forms.Control.Visible%2A> property to hide and show a control.</span></span>  
  
 [<span data-ttu-id="cdd08-117">Nasıl yapılır: Denetiminize saydam arka plan verme</span><span class="sxs-lookup"><span data-stu-id="cdd08-117">How to: Give Your Control a Transparent Background</span></span>](how-to-give-your-control-a-transparent-background.md)  
 <span data-ttu-id="cdd08-118">Nasıl kullanılacağını gösterir <xref:System.Windows.Forms.Control.SetStyle%2A> yöntemini opak, saydam veya kısmen saydam bir arka plan rengi.</span><span class="sxs-lookup"><span data-stu-id="cdd08-118">Shows how to use the <xref:System.Windows.Forms.Control.SetStyle%2A> method to create a background color that is opaque, transparent, or partially transparent.</span></span>  
  
 [<span data-ttu-id="cdd08-119">Denetimleri Görsel Stilde İşleme</span><span class="sxs-lookup"><span data-stu-id="cdd08-119">Rendering Controls with Visual Styles</span></span>](rendering-controls-with-visual-styles.md)  
 <span data-ttu-id="cdd08-120">Görsel stiller, bunları destekleyen işletim sistemlerinde kullanarak denetimleri nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="cdd08-120">Shows how to render controls using visual styles in operating systems that support them.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="cdd08-121">Başvuru</span><span class="sxs-lookup"><span data-stu-id="cdd08-121">Reference</span></span>  
 <xref:System.Windows.Forms.Control>  
 <span data-ttu-id="cdd08-122">Bu sınıf açıklar ve tüm üyeleri için bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="cdd08-122">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.UserControl>  
 <span data-ttu-id="cdd08-123">Bu sınıf açıklar ve tüm üyeleri için bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="cdd08-123">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.Control.OnPaint%2A>  
 <span data-ttu-id="cdd08-124">Bu yöntem açıklar.</span><span class="sxs-lookup"><span data-stu-id="cdd08-124">Describes this method.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="cdd08-125">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="cdd08-125">Related Sections</span></span>  
 [<span data-ttu-id="cdd08-126">Nasıl yapılır: Çizim için grafik nesneleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="cdd08-126">How to: Create Graphics Objects for Drawing</span></span>](../advanced/how-to-create-graphics-objects-for-drawing.md)  
 <span data-ttu-id="cdd08-127">Visual Studio açısından GDI + grafik işlevlerini sunar ve daha fazla bilgi için bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="cdd08-127">Introduces GDI+ graphics functionality from a Visual Studio perspective and gives links to more information.</span></span>  
  
 [<span data-ttu-id="cdd08-128">Özel Denetim Çeşitleri</span><span class="sxs-lookup"><span data-stu-id="cdd08-128">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)  
 <span data-ttu-id="cdd08-129">Özel denetimler, yazabilirsiniz türlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="cdd08-129">Describes the kinds of custom controls you can author.</span></span>
