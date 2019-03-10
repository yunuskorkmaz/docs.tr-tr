---
title: 'Nasıl yapılır: Denetim sınıfından devralma'
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- Control class [Windows Forms], inheriting from
- custom controls [Windows Forms], inheritance
- OnPaint method [Windows Forms]
- custom controls [Windows Forms], creating
ms.assetid: 46ba0df3-5cf7-443c-a3b4-a72660172476
ms.openlocfilehash: cf1b3c7d7d530710c4c7e0fbd137667c3598500a
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57702977"
---
# <a name="how-to-inherit-from-the-control-class"></a><span data-ttu-id="d5dbc-102">Nasıl yapılır: Denetim sınıfından devralma</span><span class="sxs-lookup"><span data-stu-id="d5dbc-102">How to: Inherit from the Control Class</span></span>
<span data-ttu-id="d5dbc-103">Bir Windows formunda kullanmak için tamamen özel bir denetim oluşturmak istiyorsanız, gelen alması gerektiğini <xref:System.Windows.Forms.Control> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d5dbc-103">If you want to create a completely custom control to use on a Windows Form, you should inherit from the <xref:System.Windows.Forms.Control> class.</span></span> <span data-ttu-id="d5dbc-104">Öğesinden devralan çalışırken <xref:System.Windows.Forms.Control> daha fazla planlama ve uygulama gerçekleştirmek, ayrıca, en büyük çeşitli seçenekleri sağlar sınıfını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="d5dbc-104">While inheriting from the <xref:System.Windows.Forms.Control> class requires that you perform more planning and implementation, it also provides you with the largest range of options.</span></span> <span data-ttu-id="d5dbc-105">Gelen devralınırken <xref:System.Windows.Forms.Control>, iş denetimleri yapar çok temel işlevleri devralır.</span><span class="sxs-lookup"><span data-stu-id="d5dbc-105">When inheriting from <xref:System.Windows.Forms.Control>, you inherit the very basic functionality that makes controls work.</span></span> <span data-ttu-id="d5dbc-106">Doğal olarak işlevselliğini <xref:System.Windows.Forms.Control> sınıf klavye ve fare kullanıcı girişini işleme sınırları ve denetimin boyutunu tanımlar, windows tanıtıcı sağlar ve ileti işleme ve güvenlik sağlar.</span><span class="sxs-lookup"><span data-stu-id="d5dbc-106">The functionality inherent in the <xref:System.Windows.Forms.Control> class handles user input through the keyboard and mouse, defines the bounds and size of the control, provides a windows handle, and provides message handling and security.</span></span> <span data-ttu-id="d5dbc-107">Grafik arabiriminin denetimin gerçek işleme Bu durumda olan tüm boyama birleşmez ya da herhangi bir belirli bir kullanıcı etkileşimi işlevi dahil etmez.</span><span class="sxs-lookup"><span data-stu-id="d5dbc-107">It does not incorporate any painting, which in this case is the actual rendering of the graphical interface of the control, nor does it incorporate any specific user interaction functionality.</span></span> <span data-ttu-id="d5dbc-108">Tüm özel kod aracılığıyla bu görünüşler sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d5dbc-108">You must provide all of these aspects through custom code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d5dbc-109">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="d5dbc-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="d5dbc-110">Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="d5dbc-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="d5dbc-111">Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="d5dbc-111">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-create-a-custom-control"></a><span data-ttu-id="d5dbc-112">Özel bir denetim oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="d5dbc-112">To create a custom control</span></span>  
  
1.  <span data-ttu-id="d5dbc-113">Yeni bir **Windows uygulama** veya **Windows Denetim Kitaplığı** proje.</span><span class="sxs-lookup"><span data-stu-id="d5dbc-113">Create a new **Windows Application** or **Windows Control Library** project.</span></span>  
  
2.  <span data-ttu-id="d5dbc-114">Gelen **proje** menüsünde seçin **sınıfı Ekle**.</span><span class="sxs-lookup"><span data-stu-id="d5dbc-114">From the **Project** menu, choose **Add Class**.</span></span>  
  
3.  <span data-ttu-id="d5dbc-115">İçinde **Yeni Öğe Ekle** iletişim kutusu, tıklayın **özel denetim**.</span><span class="sxs-lookup"><span data-stu-id="d5dbc-115">In the **Add New Item** dialog box, click **Custom Control**.</span></span>  
  
     <span data-ttu-id="d5dbc-116">Yeni özel denetim projenize eklenir.</span><span class="sxs-lookup"><span data-stu-id="d5dbc-116">A new custom control is added to your project.</span></span>  
  
4.  <span data-ttu-id="d5dbc-117">Açmak için F7'ye basın **Kod Düzenleyicisi** özel denetiminizin.</span><span class="sxs-lookup"><span data-stu-id="d5dbc-117">Press F7 to open the **Code Editor** for your custom control.</span></span>  
  
5.  <span data-ttu-id="d5dbc-118">Bulun <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi çağrısı dışında boş olur <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi temel sınıf.</span><span class="sxs-lookup"><span data-stu-id="d5dbc-118">Locate the <xref:System.Windows.Forms.Control.OnPaint%2A> method, which will be empty except for a call to the <xref:System.Windows.Forms.Control.OnPaint%2A> method of the base class.</span></span>  
  
6.  <span data-ttu-id="d5dbc-119">Denetim için istediğiniz herhangi bir özel boyama birleştirmek için kodu değiştirin.</span><span class="sxs-lookup"><span data-stu-id="d5dbc-119">Modify the code to incorporate any custom painting you want for your control.</span></span>  
  
     <span data-ttu-id="d5dbc-120">Grafik denetimleri için işlemek için kod yazma hakkında daha fazla bilgi için bkz: [özel denetim boyama ve işleme](custom-control-painting-and-rendering.md).</span><span class="sxs-lookup"><span data-stu-id="d5dbc-120">For information about writing code to render graphics for controls, see [Custom Control Painting and Rendering](custom-control-painting-and-rendering.md).</span></span>  
  
7.  <span data-ttu-id="d5dbc-121">Tüm özel yöntemler, özellikler veya denetiminiz birleştirecektir olayların uygulayın.</span><span class="sxs-lookup"><span data-stu-id="d5dbc-121">Implement any custom methods, properties, or events that your control will incorporate.</span></span>  
  
8.  <span data-ttu-id="d5dbc-122">Kaydet ve denetim test edin.</span><span class="sxs-lookup"><span data-stu-id="d5dbc-122">Save and test your control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5dbc-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d5dbc-123">See also</span></span>
- [<span data-ttu-id="d5dbc-124">Özel Denetim Çeşitleri</span><span class="sxs-lookup"><span data-stu-id="d5dbc-124">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
- [<span data-ttu-id="d5dbc-125">Nasıl yapılır: UserControl sınıfından devralma</span><span class="sxs-lookup"><span data-stu-id="d5dbc-125">How to: Inherit from the UserControl Class</span></span>](how-to-inherit-from-the-usercontrol-class.md)
- [<span data-ttu-id="d5dbc-126">Nasıl yapılır: Mevcut Windows Formları denetimlerinden devralma</span><span class="sxs-lookup"><span data-stu-id="d5dbc-126">How to: Inherit from Existing Windows Forms Controls</span></span>](how-to-inherit-from-existing-windows-forms-controls.md)
- [<span data-ttu-id="d5dbc-127">Nasıl yapılır: Windows Forms için yazar denetimleri</span><span class="sxs-lookup"><span data-stu-id="d5dbc-127">How to: Author Controls for Windows Forms</span></span>](how-to-author-controls-for-windows-forms.md)
- [<span data-ttu-id="d5dbc-128">Basic'de devralınmış olay işleyicileri Visual Basic sorunlarını giderme</span><span class="sxs-lookup"><span data-stu-id="d5dbc-128">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [<span data-ttu-id="d5dbc-129">Tasarım Zamanında Windows Forms Denetimleri Geliştirme</span><span class="sxs-lookup"><span data-stu-id="d5dbc-129">Developing Windows Forms Controls at Design Time</span></span>](developing-windows-forms-controls-at-design-time.md)
