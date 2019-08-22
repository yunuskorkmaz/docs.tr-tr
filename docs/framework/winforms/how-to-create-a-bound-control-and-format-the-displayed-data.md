---
title: 'Nasıl yapılır: Bağlantılı Denetim Oluşturma ve Görüntülenen Verileri Biçimlendirme'
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms], formatting
- bound controls [Windows Forms], creating
- bound controls [Windows Forms], formatting data
ms.assetid: d5a56228-899d-41d9-8af8-87b3f4ec2f94
ms.openlocfilehash: b5ad85a9477ca32cd28f246abe4ece3cace43182
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666780"
---
# <a name="how-to-create-a-bound-control-and-format-the-displayed-data"></a><span data-ttu-id="b14ca-102">Nasıl yapılır: Bağlantılı Denetim Oluşturma ve Görüntülenen Verileri Biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="b14ca-102">How to: Create a Bound Control and Format the Displayed Data</span></span>

<span data-ttu-id="b14ca-103">Windows Forms veri bağlama ile, **biçimlendirme ve Gelişmiş bağlama** iletişim kutusunu kullanarak veriye dayalı bir denetimde görünen verileri biçimlendirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b14ca-103">With Windows Forms data binding, you can format the data displayed in a data-bound control by using the **Formatting and Advanced Binding** dialog box.</span></span>

### <a name="to-bind-a-control-and-format-the-displayed-data"></a><span data-ttu-id="b14ca-104">Bir denetimi bağlamak ve görüntülenecek verileri biçimlendirmek için</span><span class="sxs-lookup"><span data-stu-id="b14ca-104">To bind a control and format the displayed data</span></span>

1. <span data-ttu-id="b14ca-105">Bir veri kaynağına bağlanın.</span><span class="sxs-lookup"><span data-stu-id="b14ca-105">Connect to a data source.</span></span>

     <span data-ttu-id="b14ca-106">Daha fazla bilgi için bkz. [veri kaynağına bağlanma](../data/adonet/connecting-to-a-data-source.md).</span><span class="sxs-lookup"><span data-stu-id="b14ca-106">For more information, see [Connecting to a Data Source](../data/adonet/connecting-to-a-data-source.md).</span></span>

2. <span data-ttu-id="b14ca-107">Formunda, denetimi seçin ve sonra Özellikler penceresi açın.</span><span class="sxs-lookup"><span data-stu-id="b14ca-107">In the form, select the control, and then open the Properties window.</span></span>

3. <span data-ttu-id="b14ca-108">**(DataBindings)** özelliğini genişletin ve sonra **(Gelişmiş)** kutusunda![üç nokta düğmesini (Visual Studio 'nun Özellikler penceresi üç nokta düğmesini (...) tıklatarak](./media/how-to-create-a-bound-control-and-format-the-displayed-data/visual-studio-ellipsis-button.png) **biçimlendirmeyi ve Gelişmiş ' i görüntüleyin.** Bu denetim için özelliklerin tamamen bir listesini içeren bağlama iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="b14ca-108">Expand the **(DataBindings)** property, and then in the **(Advanced)** box, click the ellipsis button (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/how-to-create-a-bound-control-and-format-the-displayed-data/visual-studio-ellipsis-button.png)) to display the **Formatting and Advanced Binding** dialog box, which has a complete list of properties for that control.</span></span>

4. <span data-ttu-id="b14ca-109">Bağlamak istediğiniz özelliği seçin ve sonra **bağlama** okuna tıklayın.</span><span class="sxs-lookup"><span data-stu-id="b14ca-109">Select the property you want to bind, and then click the **Binding** arrow.</span></span>

     <span data-ttu-id="b14ca-110">Kullanılabilir veri kaynaklarının bir listesi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="b14ca-110">A list of available data sources is displayed.</span></span>

5. <span data-ttu-id="b14ca-111">İstediğiniz tek veri öğesini buluncaya kadar bağlamak istediğiniz veri kaynağını genişletin.</span><span class="sxs-lookup"><span data-stu-id="b14ca-111">Expand the data source you want to bind to until you find the single data element you want.</span></span>

     <span data-ttu-id="b14ca-112">Örneğin, bir veri kümesinin tablosundaki bir sütun değerine bağlıyorsanız, veri kümesinin adını genişletin ve ardından sütun adlarını göstermek için tablo adını genişletin.</span><span class="sxs-lookup"><span data-stu-id="b14ca-112">For example, if you are binding to a column value in a dataset's table, expand the name of the dataset, and then expand the table name to display column names.</span></span>

6. <span data-ttu-id="b14ca-113">Bağlanacak öğenin adına tıklayın.</span><span class="sxs-lookup"><span data-stu-id="b14ca-113">Click the name of an element to bind to.</span></span>

7. <span data-ttu-id="b14ca-114">**Biçim türü** kutusunda, denetimde görüntülenecek verilere uygulamak istediğiniz biçime tıklayın.</span><span class="sxs-lookup"><span data-stu-id="b14ca-114">In the **Format type** box, click the format you want to apply to the data displayed in the control.</span></span>

     <span data-ttu-id="b14ca-115">Her durumda, veri kaynağı içeriyorsa <xref:System.DBNull>denetimde gösterilecek değeri belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b14ca-115">In every case, you can specify the value displayed in the control if the data source contains <xref:System.DBNull>.</span></span> <span data-ttu-id="b14ca-116">Aksi takdirde, Seçenekler, seçtiğiniz biçim türüne bağlı olarak biraz farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="b14ca-116">Otherwise, the options vary slightly, depending on the format type you choose.</span></span> <span data-ttu-id="b14ca-117">Aşağıdaki tabloda biçim türleri ve seçenekleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b14ca-117">The following table shows the format types and options.</span></span>

    |<span data-ttu-id="b14ca-118">Biçim türü</span><span class="sxs-lookup"><span data-stu-id="b14ca-118">Format type</span></span>|<span data-ttu-id="b14ca-119">Biçimlendirme seçeneği</span><span class="sxs-lookup"><span data-stu-id="b14ca-119">Formatting option</span></span>|
    |-----------------|-----------------------|
    |<span data-ttu-id="b14ca-120">Biçimlendirme yok</span><span class="sxs-lookup"><span data-stu-id="b14ca-120">No Formatting</span></span>|<span data-ttu-id="b14ca-121">Seçenek yok.</span><span class="sxs-lookup"><span data-stu-id="b14ca-121">No options.</span></span>|
    |<span data-ttu-id="b14ca-122">Numeric</span><span class="sxs-lookup"><span data-stu-id="b14ca-122">Numeric</span></span>|<span data-ttu-id="b14ca-123">Ondalık basamak sayısını artırma-azaltma denetimini kullanarak belirtin.</span><span class="sxs-lookup"><span data-stu-id="b14ca-123">Specify number of decimal places by using **Decimal places** up-down control.</span></span>|
    |<span data-ttu-id="b14ca-124">Para Birimi</span><span class="sxs-lookup"><span data-stu-id="b14ca-124">Currency</span></span>|<span data-ttu-id="b14ca-125">Ondalık basamak sayısını artırma-azaltma denetimini kullanarak belirtin.</span><span class="sxs-lookup"><span data-stu-id="b14ca-125">Specify number of decimal places by using **Decimal places** up-down control.</span></span>|
    |<span data-ttu-id="b14ca-126">Tarih saat</span><span class="sxs-lookup"><span data-stu-id="b14ca-126">Date Time</span></span>|<span data-ttu-id="b14ca-127">**Tür** seçim kutusundaki öğelerden birini seçerek tarih ve saatin nasıl görüntüleneceğini seçin.</span><span class="sxs-lookup"><span data-stu-id="b14ca-127">Select how the date and time should be displayed by selecting one of the items in the **Type** selection box.</span></span>|
    |<span data-ttu-id="b14ca-128">Bilimsel</span><span class="sxs-lookup"><span data-stu-id="b14ca-128">Scientific</span></span>|<span data-ttu-id="b14ca-129">Ondalık basamak sayısını artırma-azaltma denetimini kullanarak belirtin.</span><span class="sxs-lookup"><span data-stu-id="b14ca-129">Specify number of decimal places by using **Decimal places** up-down control.</span></span>|
    |<span data-ttu-id="b14ca-130">Özel</span><span class="sxs-lookup"><span data-stu-id="b14ca-130">Custom</span></span>|<span data-ttu-id="b14ca-131">Kullanarak bir özel biçim dizesi belirtin.</span><span class="sxs-lookup"><span data-stu-id="b14ca-131">Specify a custom format string using.</span></span><br /><br /> <span data-ttu-id="b14ca-132">Daha fazla bilgi için bkz. [biçimlendirme türleri](../../standard/base-types/formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="b14ca-132">For more information, see [Formatting Types](../../standard/base-types/formatting-types.md).</span></span> <span data-ttu-id="b14ca-133">**Not:**  Özel biçim dizelerinin, veri kaynağı ve bağlantılı denetim arasında başarılı bir şekilde gidiş dönüş garantisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="b14ca-133">**Note:**  Custom format strings are not guaranteed to successfully round trip between the data source and bound control.</span></span> <span data-ttu-id="b14ca-134">Bunun yerine bağlama <xref:System.Windows.Forms.Binding.Parse> için <xref:System.Windows.Forms.Binding.Format> veya olayını işleyin ve olay işleme kodunda özel biçimlendirme uygulayın.</span><span class="sxs-lookup"><span data-stu-id="b14ca-134">Instead handle the <xref:System.Windows.Forms.Binding.Parse> or <xref:System.Windows.Forms.Binding.Format> event for the binding and apply custom formatting in the event-handling code.</span></span>|

8. <span data-ttu-id="b14ca-135">**Biçimlendirme ve Gelişmiş bağlama** iletişim kutusunu kapatmak ve Özellikler penceresi geri dönmek için **Tamam** ' ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="b14ca-135">Click **OK** to close the **Formatting and Advanced Binding** dialog box and return to the Properties window.</span></span>

## <a name="see-also"></a><span data-ttu-id="b14ca-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b14ca-136">See also</span></span>

- [<span data-ttu-id="b14ca-137">Nasıl yapılır: Bir Windows formunda basit bağlantılı denetim oluşturma</span><span class="sxs-lookup"><span data-stu-id="b14ca-137">How to: Create a Simple-Bound Control on a Windows Form</span></span>](how-to-create-a-simple-bound-control-on-a-windows-form.md)
- [<span data-ttu-id="b14ca-138">Windows Forms'ta Kullanıcı Girdisi Doğrulama</span><span class="sxs-lookup"><span data-stu-id="b14ca-138">User Input Validation in Windows Forms</span></span>](user-input-validation-in-windows-forms.md)
- [<span data-ttu-id="b14ca-139">Windows Forms Veri Bağlama</span><span class="sxs-lookup"><span data-stu-id="b14ca-139">Windows Forms Data Binding</span></span>](windows-forms-data-binding.md)
