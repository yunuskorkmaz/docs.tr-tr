---
title: 'Nasıl yapılır: Bir Windows Formunda Basit Bağlantılı Denetim Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [Windows Forms], simple data binding
- Windows Forms controls, data binding
ms.assetid: 3bcaded8-0f1a-4cc0-8830-f59be253bf4e
ms.openlocfilehash: 26bc136ea2b7e5bda4a57c5dad65ec3522efcd3d
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44197669"
---
# <a name="how-to-create-a-simple-bound-control-on-a-windows-form"></a><span data-ttu-id="f6bf4-102">Nasıl yapılır: Bir Windows Formunda Basit Bağlantılı Denetim Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f6bf4-102">How to: Create a Simple-Bound Control on a Windows Form</span></span>
<span data-ttu-id="f6bf4-103">İle *basit bağlama*, tek bir veri öğesi, bir veri kümesi tablodaki bir sütun değeri gibi bir denetimi görüntüleme.</span><span class="sxs-lookup"><span data-stu-id="f6bf4-103">With *simple binding*, you can display a single data element, such as a column value from a dataset table, in a control.</span></span> <span data-ttu-id="f6bf4-104">Basit bir denetimin herhangi bir özelliği bir veri değerine bağlamak.</span><span class="sxs-lookup"><span data-stu-id="f6bf4-104">You can simple-bind any property of a control to a data value.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f6bf4-105">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="f6bf4-105">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="f6bf4-106">Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="f6bf4-106">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="f6bf4-107">Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="f6bf4-107">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-simple-bind-a-control"></a><span data-ttu-id="f6bf4-108">Basit-bağlama bir denetim için</span><span class="sxs-lookup"><span data-stu-id="f6bf4-108">To simple-bind a control</span></span>  
  
1.  <span data-ttu-id="f6bf4-109">Bir veri kaynağına bağlanın.</span><span class="sxs-lookup"><span data-stu-id="f6bf4-109">Connect to a data source.</span></span> <span data-ttu-id="f6bf4-110">Daha fazla bilgi için [bir veri kaynağına bağlanma](../../../docs/framework/data/adonet/connecting-to-a-data-source.md).</span><span class="sxs-lookup"><span data-stu-id="f6bf4-110">For more information, see [Connecting to a Data Source](../../../docs/framework/data/adonet/connecting-to-a-data-source.md).</span></span>  
  
2.  <span data-ttu-id="f6bf4-111">Form denetimi seçin ve görüntüleme **özellikleri** penceresi.</span><span class="sxs-lookup"><span data-stu-id="f6bf4-111">In the form, select the control and display the **Properties** window.</span></span>  
  
3.  <span data-ttu-id="f6bf4-112">Genişletin **(DataBindings)** özelliği.</span><span class="sxs-lookup"><span data-stu-id="f6bf4-112">Expand the **(DataBindings)** property.</span></span>  
  
     <span data-ttu-id="f6bf4-113">Çoğunlukla ilişkili özellikleri altında görüntülenen **(DataBindings)** özelliği.</span><span class="sxs-lookup"><span data-stu-id="f6bf4-113">The properties most often bound are displayed underneath the **(DataBindings)** property.</span></span> <span data-ttu-id="f6bf4-114">Örneğin, çoğu denetim, **metin** özelliği sık bağlı.</span><span class="sxs-lookup"><span data-stu-id="f6bf4-114">For example, in most controls, the **Text** property is most frequently bound.</span></span>  
  
4.  <span data-ttu-id="f6bf4-115">İstediğiniz özelliğin bağlama yaygın olarak bağlı özelliklerden biri değil, tıklayın **üç nokta** düğmesine (![VisualStudioEllipsesButton ekran](../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton") ) içinde **(Gelişmiş)** görüntülemek için kutusu **biçimlendirme ve Gelişmiş bağlama** bu denetim için özelliklerin tam bir liste ile iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="f6bf4-115">If the property you want to bind is not one of the commonly bound properties, click the **Ellipsis** button (![VisualStudioEllipsesButton screenshot](../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) in the **(Advanced)** box to display the **Formatting and Advanced Binding** dialog box with a complete list of properties for that control.</span></span>  
  
5.  <span data-ttu-id="f6bf4-116">Altındaki aşağı açılan oka tıklayın ve bağlamak istediğiniz özelliği seçin **bağlama**.</span><span class="sxs-lookup"><span data-stu-id="f6bf4-116">Select the property you want to bind and click the drop-down arrow under **Binding**.</span></span>  
  
     <span data-ttu-id="f6bf4-117">Kullanılabilir veri kaynaklarının bir listesi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="f6bf4-117">A list of available data sources is displayed.</span></span>  
  
6.  <span data-ttu-id="f6bf4-118">İstediğiniz tek veri öğesi bulana kadar bağlamak istediğiniz veri kaynağını genişletin.</span><span class="sxs-lookup"><span data-stu-id="f6bf4-118">Expand the data source you want to bind to until you find the single data element you want.</span></span> <span data-ttu-id="f6bf4-119">Örneğin, bir veri kümesi tablodaki bir sütun değerine bağlanıyorsanız, veri kümesinin adını genişletin ve ardından sütun adlarını görüntülemek için tablo adını genişletin.</span><span class="sxs-lookup"><span data-stu-id="f6bf4-119">For example, if you are binding to a column value in a dataset's table, expand the name of the dataset, and then expand the table name to display column names.</span></span>  
  
7.  <span data-ttu-id="f6bf4-120">Bağlanılacak bir öğe adına tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f6bf4-120">Click the name of an element to bind to.</span></span>  
  
8.  <span data-ttu-id="f6bf4-121">Üzerinde çalıştığınız varsa **biçimlendirme ve Gelişmiş bağlama** iletişim kutusu, tıklayın **Tamam** dönmek için **özellikleri** penceresi.</span><span class="sxs-lookup"><span data-stu-id="f6bf4-121">If you were working in the **Formatting and Advanced Binding** dialog box, click **OK** to return to the **Properties** window.</span></span>  
  
9. <span data-ttu-id="f6bf4-122">Denetimin ek özellikleri bağlamak istiyorsanız, 3 ila 7. adımları tekrarlayın.</span><span class="sxs-lookup"><span data-stu-id="f6bf4-122">If you want to bind additional properties of the control, repeat steps 3 through 7.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f6bf4-123">Basit veriye bağlı denetimler yalnızca bir tek veri öğesi göstermek için bir Windows formunda basit bağlantılı denetim ile gezinti mantığı içeren çok normaldir.</span><span class="sxs-lookup"><span data-stu-id="f6bf4-123">Because simple-bound controls show only a single data element, it is very typical to include navigation logic in a Windows Form with simple-bound controls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6bf4-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f6bf4-124">See Also</span></span>  
 <xref:System.Windows.Forms.Binding>  
 [<span data-ttu-id="f6bf4-125">Windows Forms Veri Bağlama</span><span class="sxs-lookup"><span data-stu-id="f6bf4-125">Windows Forms Data Binding</span></span>](../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [<span data-ttu-id="f6bf4-126">Veri Bağlama ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f6bf4-126">Data Binding and Windows Forms</span></span>](../../../docs/framework/winforms/data-binding-and-windows-forms.md)
