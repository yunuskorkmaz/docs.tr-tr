---
title: 'Nasıl yapılır: Windows Forms’ta Basit Bağlantılı Denetim Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [Windows Forms], simple data binding
- Windows Forms controls, data binding
ms.assetid: 3bcaded8-0f1a-4cc0-8830-f59be253bf4e
ms.openlocfilehash: df87f00e6e03de67c3fb1adc28472c96f4a47ef4
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015627"
---
# <a name="how-to-create-a-simple-bound-control-on-a-windows-form"></a><span data-ttu-id="7b28f-102">Nasıl yapılır: Bir Windows formunda basit bağlantılı denetim oluşturma</span><span class="sxs-lookup"><span data-stu-id="7b28f-102">How to: Create a simple-bound control on a Windows Form</span></span>

<span data-ttu-id="7b28f-103">*Basit bağlama*sayesinde, bir denetim içinde bir veri kümesi tablosundan sütun değeri gibi tek bir veri öğesi görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7b28f-103">With *simple binding*, you can display a single data element, such as a column value from a dataset table, in a control.</span></span> <span data-ttu-id="7b28f-104">Bir denetimin herhangi bir özelliğini bir veri değerine basit bir şekilde bağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7b28f-104">You can simple-bind any property of a control to a data value.</span></span>

## <a name="to-simple-bind-a-control"></a><span data-ttu-id="7b28f-105">Bir denetimi basit bağlamak için</span><span class="sxs-lookup"><span data-stu-id="7b28f-105">To simple-bind a control</span></span>

1. <span data-ttu-id="7b28f-106">Bir veri kaynağına bağlanın.</span><span class="sxs-lookup"><span data-stu-id="7b28f-106">Connect to a data source.</span></span> <span data-ttu-id="7b28f-107">Daha fazla bilgi için bkz. [veri kaynağına bağlanma](../data/adonet/connecting-to-a-data-source.md).</span><span class="sxs-lookup"><span data-stu-id="7b28f-107">For more information, see [Connecting to a Data Source](../data/adonet/connecting-to-a-data-source.md).</span></span>

2. <span data-ttu-id="7b28f-108">Visual Studio 'da, formdaki denetimi seçin ve **Özellikler** penceresini görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="7b28f-108">In Visual Studio, select the control on the form and display the **Properties** window.</span></span>

3. <span data-ttu-id="7b28f-109">**(DataBindings)** özelliğini genişletin.</span><span class="sxs-lookup"><span data-stu-id="7b28f-109">Expand the **(DataBindings)** property.</span></span>

     <span data-ttu-id="7b28f-110">En sık ciltleyen Özellikler **(DataBindings)** özelliğinin altında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="7b28f-110">The properties most often bound are displayed underneath the **(DataBindings)** property.</span></span> <span data-ttu-id="7b28f-111">Örneğin, çoğu denetimin **metin** özelliği en sık bağlanır.</span><span class="sxs-lookup"><span data-stu-id="7b28f-111">For example, in most controls, the **Text** property is most frequently bound.</span></span>

4. <span data-ttu-id="7b28f-112">Bağlamak istediğiniz özellik, yaygın olarak bağlanan özelliklerden biri değilse, **(Gelişmiş)** kutusunda![](./media/how-to-create-a-simple-bound-control-on-a-windows-form/visual-studio-ellipsis-button.png) **bulunan üç nokta düğmesine (Visual Studio Özellikler penceresi) (...) tıklayın. Biçimlendirme ve Gelişmiş bağlama** iletişim kutusu, bu denetimin özelliklerinin tamamı listesi.</span><span class="sxs-lookup"><span data-stu-id="7b28f-112">If the property you want to bind is not one of the commonly bound properties, click the **Ellipsis** button (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/how-to-create-a-simple-bound-control-on-a-windows-form/visual-studio-ellipsis-button.png)) in the **(Advanced)** box to display the **Formatting and Advanced Binding** dialog box with a complete list of properties for that control.</span></span>

5. <span data-ttu-id="7b28f-113">Bağlamak istediğiniz özelliği seçin ve **bağlama**bölümündeki aşağı açılan oka tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7b28f-113">Select the property you want to bind and click the drop-down arrow under **Binding**.</span></span>

     <span data-ttu-id="7b28f-114">Kullanılabilir veri kaynaklarının bir listesi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="7b28f-114">A list of available data sources is displayed.</span></span>

6. <span data-ttu-id="7b28f-115">İstediğiniz tek veri öğesini buluncaya kadar bağlamak istediğiniz veri kaynağını genişletin.</span><span class="sxs-lookup"><span data-stu-id="7b28f-115">Expand the data source you want to bind to until you find the single data element you want.</span></span> <span data-ttu-id="7b28f-116">Örneğin, bir veri kümesinin tablosundaki bir sütun değerine bağlıyorsanız, veri kümesinin adını genişletin ve ardından sütun adlarını göstermek için tablo adını genişletin.</span><span class="sxs-lookup"><span data-stu-id="7b28f-116">For example, if you are binding to a column value in a dataset's table, expand the name of the dataset, and then expand the table name to display column names.</span></span>

7. <span data-ttu-id="7b28f-117">Bağlanacak öğenin adına tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7b28f-117">Click the name of an element to bind to.</span></span>

8. <span data-ttu-id="7b28f-118">**Biçimlendirme ve Gelişmiş bağlama** iletişim kutusunda çalışıyorsanız, **Özellikler** penceresine dönmek için **Tamam** ' ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="7b28f-118">If you were working in the **Formatting and Advanced Binding** dialog box, click **OK** to return to the **Properties** window.</span></span>

9. <span data-ttu-id="7b28f-119">Denetimin ek özelliklerini bağlamak istiyorsanız 3 ile 7 arasındaki adımları yineleyin.</span><span class="sxs-lookup"><span data-stu-id="7b28f-119">If you want to bind additional properties of the control, repeat steps 3 through 7.</span></span>

    > [!NOTE]
    > <span data-ttu-id="7b28f-120">Basit-bağlantılı denetimler yalnızca tek bir veri öğesi gösterebildiğinden, basit bağlantılı denetimlerle bir Windows formuna gezinme mantığını eklemek çok normaldir.</span><span class="sxs-lookup"><span data-stu-id="7b28f-120">Because simple-bound controls show only a single data element, it is very typical to include navigation logic in a Windows Form with simple-bound controls.</span></span>

## <a name="see-also"></a><span data-ttu-id="7b28f-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7b28f-121">See also</span></span>

- <xref:System.Windows.Forms.Binding>
- [<span data-ttu-id="7b28f-122">Windows Forms Veri Bağlama</span><span class="sxs-lookup"><span data-stu-id="7b28f-122">Windows Forms Data Binding</span></span>](windows-forms-data-binding.md)
- [<span data-ttu-id="7b28f-123">Veri Bağlama ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7b28f-123">Data Binding and Windows Forms</span></span>](data-binding-and-windows-forms.md)
