---
title: 'Nasıl yapılır: Control Sınıfından Devralma'
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- Control class [Windows Forms], inheriting from
- custom controls [Windows Forms], inheritance
- OnPaint method [Windows Forms]
- custom controls [Windows Forms], creating
ms.assetid: 46ba0df3-5cf7-443c-a3b4-a72660172476
ms.openlocfilehash: 0cb63be6774fd82cd94a1bc59b8a1025efa47df5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966577"
---
# <a name="how-to-inherit-from-the-control-class"></a><span data-ttu-id="dec7d-102">Nasıl yapılır: Control Sınıfından Devralma</span><span class="sxs-lookup"><span data-stu-id="dec7d-102">How to: Inherit from the Control Class</span></span>
<span data-ttu-id="dec7d-103">Bir Windows formunda kullanmak üzere tamamen özel bir denetim oluşturmak isterseniz, <xref:System.Windows.Forms.Control> sınıfından ' ı devralması gerekir.</span><span class="sxs-lookup"><span data-stu-id="dec7d-103">If you want to create a completely custom control to use on a Windows Form, you should inherit from the <xref:System.Windows.Forms.Control> class.</span></span> <span data-ttu-id="dec7d-104"><xref:System.Windows.Forms.Control> Sınıfından devralma işlemi daha fazla planlama ve uygulama gerçekleştirmenizi gerektirdiğinden, size en fazla seçenek aralığını da sağlar.</span><span class="sxs-lookup"><span data-stu-id="dec7d-104">While inheriting from the <xref:System.Windows.Forms.Control> class requires that you perform more planning and implementation, it also provides you with the largest range of options.</span></span> <span data-ttu-id="dec7d-105">' Dan <xref:System.Windows.Forms.Control>devralırken, denetimlerin çalışmasını sağlayan temel işlevsellikleri devralırsınız.</span><span class="sxs-lookup"><span data-stu-id="dec7d-105">When inheriting from <xref:System.Windows.Forms.Control>, you inherit the very basic functionality that makes controls work.</span></span> <span data-ttu-id="dec7d-106"><xref:System.Windows.Forms.Control> Sınıfında devralınan işlevler, klavye ve fare aracılığıyla Kullanıcı girişini işler, denetimin sınırlarını ve boyutunu tanımlar, bir Windows tutamacı sağlar ve ileti işleme ve güvenlik sağlar.</span><span class="sxs-lookup"><span data-stu-id="dec7d-106">The functionality inherent in the <xref:System.Windows.Forms.Control> class handles user input through the keyboard and mouse, defines the bounds and size of the control, provides a windows handle, and provides message handling and security.</span></span> <span data-ttu-id="dec7d-107">Bu, denetimin grafik arabiriminin gerçek işlemesi olan veya belirli kullanıcı etkileşimi işlevlerini dahil eden herhangi bir boyama içermez.</span><span class="sxs-lookup"><span data-stu-id="dec7d-107">It does not incorporate any painting, which in this case is the actual rendering of the graphical interface of the control, nor does it incorporate any specific user interaction functionality.</span></span> <span data-ttu-id="dec7d-108">Bu yönlerinin tümünü özel kod aracılığıyla sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="dec7d-108">You must provide all of these aspects through custom code.</span></span>

## <a name="to-create-a-custom-control"></a><span data-ttu-id="dec7d-109">Özel bir denetim oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="dec7d-109">To create a custom control</span></span>

1. <span data-ttu-id="dec7d-110">Yeni bir **Windows uygulaması** veya **Windows Denetim Kitaplığı** projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="dec7d-110">Create a new **Windows Application** or **Windows Control Library** project.</span></span>

2. <span data-ttu-id="dec7d-111">**Proje** menüsünden **Sınıf Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="dec7d-111">From the **Project** menu, choose **Add Class**.</span></span>

3. <span data-ttu-id="dec7d-112">**Yeni öğe Ekle** Iletişim kutusunda **özel denetim ' e**tıklayın.</span><span class="sxs-lookup"><span data-stu-id="dec7d-112">In the **Add New Item** dialog box, click **Custom Control**.</span></span>

     <span data-ttu-id="dec7d-113">Projenize yeni bir özel denetim eklenir.</span><span class="sxs-lookup"><span data-stu-id="dec7d-113">A new custom control is added to your project.</span></span>

4. <span data-ttu-id="dec7d-114">Özel denetiminizin **kod düzenleyicisini** açmak için F7 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="dec7d-114">Press F7 to open the **Code Editor** for your custom control.</span></span>

5. <span data-ttu-id="dec7d-115">Temel sınıf <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemine yapılan bir çağrı dışında boş olacak yöntemibulun.<xref:System.Windows.Forms.Control.OnPaint%2A></span><span class="sxs-lookup"><span data-stu-id="dec7d-115">Locate the <xref:System.Windows.Forms.Control.OnPaint%2A> method, which will be empty except for a call to the <xref:System.Windows.Forms.Control.OnPaint%2A> method of the base class.</span></span>

6. <span data-ttu-id="dec7d-116">Denetiminiz için istediğiniz özel boyamayı içerecek şekilde kodu değiştirin.</span><span class="sxs-lookup"><span data-stu-id="dec7d-116">Modify the code to incorporate any custom painting you want for your control.</span></span>

     <span data-ttu-id="dec7d-117">Denetimler için grafik işlemek üzere kod yazma hakkında daha fazla bilgi için bkz. [özel denetim boyama ve işleme](custom-control-painting-and-rendering.md).</span><span class="sxs-lookup"><span data-stu-id="dec7d-117">For information about writing code to render graphics for controls, see [Custom Control Painting and Rendering](custom-control-painting-and-rendering.md).</span></span>

7. <span data-ttu-id="dec7d-118">Denetiminizin dahil olacağı özel yöntemleri, özellikleri veya olayları uygulayın.</span><span class="sxs-lookup"><span data-stu-id="dec7d-118">Implement any custom methods, properties, or events that your control will incorporate.</span></span>

8. <span data-ttu-id="dec7d-119">Denetiminizi kaydedin ve test edin.</span><span class="sxs-lookup"><span data-stu-id="dec7d-119">Save and test your control.</span></span>

## <a name="see-also"></a><span data-ttu-id="dec7d-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dec7d-120">See also</span></span>

- [<span data-ttu-id="dec7d-121">Özel Denetim Çeşitleri</span><span class="sxs-lookup"><span data-stu-id="dec7d-121">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
- [<span data-ttu-id="dec7d-122">Nasıl yapılır: UserControl sınıfından devralma</span><span class="sxs-lookup"><span data-stu-id="dec7d-122">How to: Inherit from the UserControl Class</span></span>](how-to-inherit-from-the-usercontrol-class.md)
- [<span data-ttu-id="dec7d-123">Nasıl yapılır: Mevcut Windows Forms denetimlerinden devralma</span><span class="sxs-lookup"><span data-stu-id="dec7d-123">How to: Inherit from Existing Windows Forms Controls</span></span>](how-to-inherit-from-existing-windows-forms-controls.md)
- [<span data-ttu-id="dec7d-124">Nasıl yapılır: Windows Forms için yazar denetimleri</span><span class="sxs-lookup"><span data-stu-id="dec7d-124">How to: Author Controls for Windows Forms</span></span>](how-to-author-controls-for-windows-forms.md)
- [<span data-ttu-id="dec7d-125">Visual Basic devralınan olay Işleyicileriyle ilgili sorunları giderme</span><span class="sxs-lookup"><span data-stu-id="dec7d-125">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [<span data-ttu-id="dec7d-126">Tasarım Zamanında Windows Forms Denetimleri Geliştirme</span><span class="sxs-lookup"><span data-stu-id="dec7d-126">Developing Windows Forms Controls at Design Time</span></span>](developing-windows-forms-controls-at-design-time.md)
