---
title: 'Nasıl yapılır: Bağlantılı Denetim Oluşturma ve Görüntülenen Verileri Biçimlendirme'
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms], formatting
- bound controls [Windows Forms], creating
- bound controls [Windows Forms], formatting data
ms.assetid: d5a56228-899d-41d9-8af8-87b3f4ec2f94
ms.openlocfilehash: 8f4d3c4c738e31ab83d506dc7afb4e49b142765b
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2018
ms.locfileid: "44508016"
---
# <a name="how-to-create-a-bound-control-and-format-the-displayed-data"></a><span data-ttu-id="9c51a-102">Nasıl yapılır: Bağlantılı Denetim Oluşturma ve Görüntülenen Verileri Biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="9c51a-102">How to: Create a Bound Control and Format the Displayed Data</span></span>
<span data-ttu-id="9c51a-103">Windows Forms veri bağlama ile kullanarak bir veri bağlı denetim içinde görüntülenen verileri biçimlendirebilirsiniz **biçimlendirme ve Gelişmiş bağlama** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="9c51a-103">With Windows Forms data binding, you can format the data displayed in a data-bound control by using the **Formatting and Advanced Binding** dialog box.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9c51a-104">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="9c51a-104">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="9c51a-105">Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="9c51a-105">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="9c51a-106">Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="9c51a-106">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-bind-a-control-and-format-the-displayed-data"></a><span data-ttu-id="9c51a-107">Bir denetimi bağlama ve görüntülenen verileri biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="9c51a-107">To bind a control and format the displayed data</span></span>  
  
1.  <span data-ttu-id="9c51a-108">Bir veri kaynağına bağlanın.</span><span class="sxs-lookup"><span data-stu-id="9c51a-108">Connect to a data source.</span></span>  
  
     <span data-ttu-id="9c51a-109">Daha fazla bilgi için [bir veri kaynağına bağlanma](../../../docs/framework/data/adonet/connecting-to-a-data-source.md).</span><span class="sxs-lookup"><span data-stu-id="9c51a-109">For more information, see [Connecting to a Data Source](../../../docs/framework/data/adonet/connecting-to-a-data-source.md).</span></span>  
  
2.  <span data-ttu-id="9c51a-110">Form denetimi seçin ve ardından Özellikler penceresini açın.</span><span class="sxs-lookup"><span data-stu-id="9c51a-110">In the form, select the control, and then open the Properties window.</span></span>  
  
3.  <span data-ttu-id="9c51a-111">Genişletin **(DataBindings)** özelliği ve ardından **(Gelişmiş)** kutusunda, üç nokta düğmesini (![VisualStudioEllipsesButton ekran](../../../docs/framework/winforms/media/vbellipsesbutton.png " vbEllipsesButton")) görüntülenecek **biçimlendirme ve Gelişmiş bağlama** iletişim kutusunda, bu denetimin özelliklerini tam bir listesi bulunur.</span><span class="sxs-lookup"><span data-stu-id="9c51a-111">Expand the **(DataBindings)** property, and then in the **(Advanced)** box, click the ellipsis button (![VisualStudioEllipsesButton screenshot](../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) to display the **Formatting and Advanced Binding** dialog box, which has a complete list of properties for that control.</span></span>  
  
4.  <span data-ttu-id="9c51a-112">Bağlama ve ardından istediğiniz özelliği seçin **bağlama** oku.</span><span class="sxs-lookup"><span data-stu-id="9c51a-112">Select the property you want to bind, and then click the **Binding** arrow.</span></span>  
  
     <span data-ttu-id="9c51a-113">Kullanılabilir veri kaynaklarının bir listesi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="9c51a-113">A list of available data sources is displayed.</span></span>  
  
5.  <span data-ttu-id="9c51a-114">İstediğiniz tek veri öğesi bulana kadar bağlamak istediğiniz veri kaynağını genişletin.</span><span class="sxs-lookup"><span data-stu-id="9c51a-114">Expand the data source you want to bind to until you find the single data element you want.</span></span>  
  
     <span data-ttu-id="9c51a-115">Örneğin, bir veri kümesi tablodaki bir sütun değerine bağlanıyorsanız, veri kümesinin adını genişletin ve ardından sütun adlarını görüntülemek için tablo adını genişletin.</span><span class="sxs-lookup"><span data-stu-id="9c51a-115">For example, if you are binding to a column value in a dataset's table, expand the name of the dataset, and then expand the table name to display column names.</span></span>  
  
6.  <span data-ttu-id="9c51a-116">Bağlanılacak bir öğe adına tıklayın.</span><span class="sxs-lookup"><span data-stu-id="9c51a-116">Click the name of an element to bind to.</span></span>  
  
7.  <span data-ttu-id="9c51a-117">İçinde **türünü biçimlendirme** kutusunda, denetimde görüntülenen verilere uygulamak istediğiniz biçime tıklayın.</span><span class="sxs-lookup"><span data-stu-id="9c51a-117">In the **Format type** box, click the format you want to apply to the data displayed in the control.</span></span>  
  
     <span data-ttu-id="9c51a-118">Her durumda, veri kaynağı içeriyorsa denetimde görüntülenen değeri belirtebilirsiniz <xref:System.DBNull>.</span><span class="sxs-lookup"><span data-stu-id="9c51a-118">In every case, you can specify the value displayed in the control if the data source contains <xref:System.DBNull>.</span></span> <span data-ttu-id="9c51a-119">Aksi takdirde, Seçenekler, seçtiğiniz biçim türüne bağlı olarak biraz değişir.</span><span class="sxs-lookup"><span data-stu-id="9c51a-119">Otherwise, the options vary slightly, depending on the format type you choose.</span></span> <span data-ttu-id="9c51a-120">Biçimlendirme türleri ve seçenekleri aşağıdaki tabloda gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="9c51a-120">The following table shows the format types and options.</span></span>  
  
    |<span data-ttu-id="9c51a-121">Biçim türü</span><span class="sxs-lookup"><span data-stu-id="9c51a-121">Format type</span></span>|<span data-ttu-id="9c51a-122">Biçimlendirme seçeneği</span><span class="sxs-lookup"><span data-stu-id="9c51a-122">Formatting option</span></span>|  
    |-----------------|-----------------------|  
    |<span data-ttu-id="9c51a-123">Biçimlendirme yok</span><span class="sxs-lookup"><span data-stu-id="9c51a-123">No Formatting</span></span>|<span data-ttu-id="9c51a-124">Seçenek yok.</span><span class="sxs-lookup"><span data-stu-id="9c51a-124">No options.</span></span>|  
    |<span data-ttu-id="9c51a-125">Sayısal</span><span class="sxs-lookup"><span data-stu-id="9c51a-125">Numeric</span></span>|<span data-ttu-id="9c51a-126">Ondalık basamak sayısını kullanarak belirtin **ondalık** yukarı-aşağı denetimi.</span><span class="sxs-lookup"><span data-stu-id="9c51a-126">Specify number of decimal places by using **Decimal places** up-down control.</span></span>|  
    |<span data-ttu-id="9c51a-127">Para Birimi</span><span class="sxs-lookup"><span data-stu-id="9c51a-127">Currency</span></span>|<span data-ttu-id="9c51a-128">Ondalık basamak sayısını kullanarak belirtin **ondalık** yukarı-aşağı denetimi.</span><span class="sxs-lookup"><span data-stu-id="9c51a-128">Specify number of decimal places by using **Decimal places** up-down control.</span></span>|  
    |<span data-ttu-id="9c51a-129">Tarih saat</span><span class="sxs-lookup"><span data-stu-id="9c51a-129">Date Time</span></span>|<span data-ttu-id="9c51a-130">Nasıl tarih ve saat öğelerden birini seçerek görüntüleneceğini seçin **türü** seçim kutusu.</span><span class="sxs-lookup"><span data-stu-id="9c51a-130">Select how the date and time should be displayed by selecting one of the items in the **Type** selection box.</span></span>|  
    |<span data-ttu-id="9c51a-131">Bilimsel</span><span class="sxs-lookup"><span data-stu-id="9c51a-131">Scientific</span></span>|<span data-ttu-id="9c51a-132">Ondalık basamak sayısını kullanarak belirtin **ondalık** yukarı-aşağı denetimi.</span><span class="sxs-lookup"><span data-stu-id="9c51a-132">Specify number of decimal places by using **Decimal places** up-down control.</span></span>|  
    |<span data-ttu-id="9c51a-133">Özel</span><span class="sxs-lookup"><span data-stu-id="9c51a-133">Custom</span></span>|<span data-ttu-id="9c51a-134">Kullanarak bir özel biçim dizesi belirtin.</span><span class="sxs-lookup"><span data-stu-id="9c51a-134">Specify a custom format string using.</span></span><br /><br /> <span data-ttu-id="9c51a-135">Daha fazla bilgi için [biçimlendirme türleri](../../../docs/standard/base-types/formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="9c51a-135">For more information, see [Formatting Types](../../../docs/standard/base-types/formatting-types.md).</span></span> <span data-ttu-id="9c51a-136">**Not:** özel biçim dizeleri başarıyla ilişkili denetim ve veri kaynağı arasında gidiş dönüş için garanti edilmez.</span><span class="sxs-lookup"><span data-stu-id="9c51a-136">**Note:**  Custom format strings are not guaranteed to successfully round trip between the data source and bound control.</span></span> <span data-ttu-id="9c51a-137">Bunun yerine işlemek <xref:System.Windows.Forms.Binding.Parse> veya <xref:System.Windows.Forms.Binding.Format> bağlama için olay ve olay işleme kodda özel biçimlendirme uygulayın.</span><span class="sxs-lookup"><span data-stu-id="9c51a-137">Instead handle the <xref:System.Windows.Forms.Binding.Parse> or <xref:System.Windows.Forms.Binding.Format> event for the binding and apply custom formatting in the event-handling code.</span></span>|  
  
8.  <span data-ttu-id="9c51a-138">Tıklayın **Tamam** kapatmak için **biçimlendirme ve Gelişmiş bağlama** iletişim kutusu ve Özellikler penceresinin başı.</span><span class="sxs-lookup"><span data-stu-id="9c51a-138">Click **OK** to close the **Formatting and Advanced Binding** dialog box and return to the Properties window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c51a-139">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9c51a-139">See Also</span></span>  
 [<span data-ttu-id="9c51a-140">Nasıl yapılır: Bir Windows Formunda Basit Bağlantılı Denetim Oluşturma</span><span class="sxs-lookup"><span data-stu-id="9c51a-140">How to: Create a Simple-Bound Control on a Windows Form</span></span>](../../../docs/framework/winforms/how-to-create-a-simple-bound-control-on-a-windows-form.md)  
 [<span data-ttu-id="9c51a-141">Windows Forms'ta Kullanıcı Girdisi Doğrulama</span><span class="sxs-lookup"><span data-stu-id="9c51a-141">User Input Validation in Windows Forms</span></span>](../../../docs/framework/winforms/user-input-validation-in-windows-forms.md)  
 [<span data-ttu-id="9c51a-142">Windows Forms Veri Bağlama</span><span class="sxs-lookup"><span data-stu-id="9c51a-142">Windows Forms Data Binding</span></span>](../../../docs/framework/winforms/windows-forms-data-binding.md)
