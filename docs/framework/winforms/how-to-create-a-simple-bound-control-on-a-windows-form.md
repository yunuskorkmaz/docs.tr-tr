---
title: 'Nasıl yapılır: Bir Windows Formunda Basit Bağlantılı Denetim Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [Windows Forms], simple data binding
- Windows Forms controls, data binding
ms.assetid: 3bcaded8-0f1a-4cc0-8830-f59be253bf4e
ms.openlocfilehash: ce4585a1c5c2b9acbdb7ec33c62a1e91851b720e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33538838"
---
# <a name="how-to-create-a-simple-bound-control-on-a-windows-form"></a><span data-ttu-id="5d958-102">Nasıl yapılır: Bir Windows Formunda Basit Bağlantılı Denetim Oluşturma</span><span class="sxs-lookup"><span data-stu-id="5d958-102">How to: Create a Simple-Bound Control on a Windows Form</span></span>
<span data-ttu-id="5d958-103">İle *basit bağlama*, tek bir veri öğesi, bir veri kümesi tablodaki bir sütun değeri gibi bir denetimi görüntüleme.</span><span class="sxs-lookup"><span data-stu-id="5d958-103">With *simple binding*, you can display a single data element, such as a column value from a dataset table, in a control.</span></span> <span data-ttu-id="5d958-104">Basit bir denetim herhangi bir özelliği bir veri değerine Bağ.</span><span class="sxs-lookup"><span data-stu-id="5d958-104">You can simple-bind any property of a control to a data value.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5d958-105">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="5d958-105">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="5d958-106">Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="5d958-106">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="5d958-107">Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="5d958-107">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-simple-bind-a-control"></a><span data-ttu-id="5d958-108">Basit-Denetim bağlamak için</span><span class="sxs-lookup"><span data-stu-id="5d958-108">To simple-bind a control</span></span>  
  
1.  <span data-ttu-id="5d958-109">Bir veri kaynağına bağlanın.</span><span class="sxs-lookup"><span data-stu-id="5d958-109">Connect to a data source.</span></span> <span data-ttu-id="5d958-110">Daha fazla bilgi için bkz: [bir veri kaynağına bağlanma](../../../docs/framework/data/adonet/connecting-to-a-data-source.md).</span><span class="sxs-lookup"><span data-stu-id="5d958-110">For more information, see [Connecting to a Data Source](../../../docs/framework/data/adonet/connecting-to-a-data-source.md).</span></span>  
  
2.  <span data-ttu-id="5d958-111">Form denetimi seçin ve görüntüleme **özellikleri** penceresi.</span><span class="sxs-lookup"><span data-stu-id="5d958-111">In the form, select the control and display the **Properties** window.</span></span>  
  
3.  <span data-ttu-id="5d958-112">Genişletme **(veri bağlamaları)** özelliği.</span><span class="sxs-lookup"><span data-stu-id="5d958-112">Expand the **(DataBindings)** property.</span></span>  
  
     <span data-ttu-id="5d958-113">En sık bağlı özellikleri altında görüntülenir **(veri bağlamaları)** özelliği.</span><span class="sxs-lookup"><span data-stu-id="5d958-113">The properties most often bound are displayed underneath the **(DataBindings)** property.</span></span> <span data-ttu-id="5d958-114">Örneğin, çoğu denetimleri içinde **metin** özelliği en sık bağlı.</span><span class="sxs-lookup"><span data-stu-id="5d958-114">For example, in most controls, the **Text** property is most frequently bound.</span></span>  
  
4.  <span data-ttu-id="5d958-115">Özelliği, istiyorsanız bağlama yaygın olarak bağlanmış özelliklerin biri değil,'ı tıklatın **üç nokta** düğmesi (![VisualStudioEllipsesButton ekran](../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton") ) içinde **(Gelişmiş)** görüntülemek için kutusunu **biçimlendirme ve Gelişmiş bağlama** bu denetim için özelliklerin tam bir listesi ile iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="5d958-115">If the property you want to bind is not one of the commonly bound properties, click the **Ellipsis** button (![VisualStudioEllipsesButton screenshot](../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) in the **(Advanced)** box to display the **Formatting and Advanced Binding** dialog box with a complete list of properties for that control.</span></span>  
  
5.  <span data-ttu-id="5d958-116">Altında aşağı açılan okunu tıklatıp bağlamak istediğiniz özelliği seçin **bağlama**.</span><span class="sxs-lookup"><span data-stu-id="5d958-116">Select the property you want to bind and click the drop-down arrow under **Binding**.</span></span>  
  
     <span data-ttu-id="5d958-117">Kullanılabilir veri kaynaklarının listesi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="5d958-117">A list of available data sources is displayed.</span></span>  
  
6.  <span data-ttu-id="5d958-118">İstediğiniz tek bir veri öğesi bulana kadar bağlamak istediğiniz veri kaynağı'nı genişletin.</span><span class="sxs-lookup"><span data-stu-id="5d958-118">Expand the data source you want to bind to until you find the single data element you want.</span></span> <span data-ttu-id="5d958-119">Örneğin, bir veri kümesi'nin tablodaki bir sütun değerine bağlanıyorsanız, veri kümesinin adını genişletin ve ardından sütun adlarını görüntülemek için tablo adını genişletin.</span><span class="sxs-lookup"><span data-stu-id="5d958-119">For example, if you are binding to a column value in a dataset's table, expand the name of the dataset, and then expand the table name to display column names.</span></span>  
  
7.  <span data-ttu-id="5d958-120">Bağlanacak bir öğenin adına tıklayın.</span><span class="sxs-lookup"><span data-stu-id="5d958-120">Click the name of an element to bind to.</span></span>  
  
8.  <span data-ttu-id="5d958-121">Çalışmakta olduğunuz varsa **biçimlendirme ve Gelişmiş bağlama** iletişim kutusu, tıklatın **Tamam** geri dönmek için **özellikleri** penceresi.</span><span class="sxs-lookup"><span data-stu-id="5d958-121">If you were working in the **Formatting and Advanced Binding** dialog box, click **OK** to return to the **Properties** window.</span></span>  
  
9. <span data-ttu-id="5d958-122">Denetimin ek özellikler bağlamak istiyorsanız, 3 ile 7 arasındaki adımları yineleyin.</span><span class="sxs-lookup"><span data-stu-id="5d958-122">If you want to bind additional properties of the control, repeat steps 3 through 7.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5d958-123">Yalnızca tek bir veri öğesi basit-bağlama denetimleri göstermek için bir Windows formunda basit bağlantılı denetimleri ile gezinti mantığı dahil çok normaldir.</span><span class="sxs-lookup"><span data-stu-id="5d958-123">Because simple-bound controls show only a single data element, it is very typical to include navigation logic in a Windows Form with simple-bound controls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d958-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5d958-124">See Also</span></span>  
 <xref:System.Windows.Forms.Binding>  
 [<span data-ttu-id="5d958-125">Windows Forms Veri Bağlama</span><span class="sxs-lookup"><span data-stu-id="5d958-125">Windows Forms Data Binding</span></span>](../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [<span data-ttu-id="5d958-126">Veri Bağlama ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5d958-126">Data Binding and Windows Forms</span></span>](../../../docs/framework/winforms/data-binding-and-windows-forms.md)
