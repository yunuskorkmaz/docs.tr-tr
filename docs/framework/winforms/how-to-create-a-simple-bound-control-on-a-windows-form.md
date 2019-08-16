---
title: 'Nasıl yapılır: Windows Forms’ta Basit Bağlantılı Denetim Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [Windows Forms], simple data binding
- Windows Forms controls, data binding
ms.assetid: 3bcaded8-0f1a-4cc0-8830-f59be253bf4e
ms.openlocfilehash: ed1d0e423a3cdf77a242ec3214720f1466f65897
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039502"
---
# <a name="how-to-create-a-simple-bound-control-on-a-windows-form"></a><span data-ttu-id="da743-102">Nasıl yapılır: Windows Forms’ta Basit Bağlantılı Denetim Oluşturma</span><span class="sxs-lookup"><span data-stu-id="da743-102">How to: Create a Simple-Bound Control on a Windows Form</span></span>

<span data-ttu-id="da743-103">*Basit bağlama*sayesinde, bir denetim içinde bir veri kümesi tablosundan sütun değeri gibi tek bir veri öğesi görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="da743-103">With *simple binding*, you can display a single data element, such as a column value from a dataset table, in a control.</span></span> <span data-ttu-id="da743-104">Bir denetimin herhangi bir özelliğini bir veri değerine basit bir şekilde bağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="da743-104">You can simple-bind any property of a control to a data value.</span></span>

### <a name="to-simple-bind-a-control"></a><span data-ttu-id="da743-105">Bir denetimi basit bağlamak için</span><span class="sxs-lookup"><span data-stu-id="da743-105">To simple-bind a control</span></span>

1. <span data-ttu-id="da743-106">Bir veri kaynağına bağlanın.</span><span class="sxs-lookup"><span data-stu-id="da743-106">Connect to a data source.</span></span> <span data-ttu-id="da743-107">Daha fazla bilgi için bkz. [veri kaynağına bağlanma](../data/adonet/connecting-to-a-data-source.md).</span><span class="sxs-lookup"><span data-stu-id="da743-107">For more information, see [Connecting to a Data Source](../data/adonet/connecting-to-a-data-source.md).</span></span>

2. <span data-ttu-id="da743-108">Formunda, denetimi seçin ve **Özellikler** penceresini görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="da743-108">In the form, select the control and display the **Properties** window.</span></span>

3. <span data-ttu-id="da743-109">**(DataBindings)** özelliğini genişletin.</span><span class="sxs-lookup"><span data-stu-id="da743-109">Expand the **(DataBindings)** property.</span></span>

     <span data-ttu-id="da743-110">En sık ciltleyen Özellikler **(DataBindings)** özelliğinin altında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="da743-110">The properties most often bound are displayed underneath the **(DataBindings)** property.</span></span> <span data-ttu-id="da743-111">Örneğin, çoğu denetimin **metin** özelliği en sık bağlanır.</span><span class="sxs-lookup"><span data-stu-id="da743-111">For example, in most controls, the **Text** property is most frequently bound.</span></span>

4. <span data-ttu-id="da743-112">Bağlamak istediğiniz özellik, yaygın olarak bağlanan özelliklerden biri değilse, **(Gelişmiş)** kutusunda![](./media/how-to-create-a-simple-bound-control-on-a-windows-form/visual-studio-ellipsis-button.png) **bulunan üç nokta düğmesine (Visual Studio Özellikler penceresi) (...) tıklayın. Biçimlendirme ve Gelişmiş bağlama** iletişim kutusu, bu denetimin özelliklerinin tamamı listesi.</span><span class="sxs-lookup"><span data-stu-id="da743-112">If the property you want to bind is not one of the commonly bound properties, click the **Ellipsis** button (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/how-to-create-a-simple-bound-control-on-a-windows-form/visual-studio-ellipsis-button.png)) in the **(Advanced)** box to display the **Formatting and Advanced Binding** dialog box with a complete list of properties for that control.</span></span>

5. <span data-ttu-id="da743-113">Bağlamak istediğiniz özelliği seçin ve **bağlama**bölümündeki aşağı açılan oka tıklayın.</span><span class="sxs-lookup"><span data-stu-id="da743-113">Select the property you want to bind and click the drop-down arrow under **Binding**.</span></span>

     <span data-ttu-id="da743-114">Kullanılabilir veri kaynaklarının bir listesi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="da743-114">A list of available data sources is displayed.</span></span>

6. <span data-ttu-id="da743-115">İstediğiniz tek veri öğesini buluncaya kadar bağlamak istediğiniz veri kaynağını genişletin.</span><span class="sxs-lookup"><span data-stu-id="da743-115">Expand the data source you want to bind to until you find the single data element you want.</span></span> <span data-ttu-id="da743-116">Örneğin, bir veri kümesinin tablosundaki bir sütun değerine bağlıyorsanız, veri kümesinin adını genişletin ve ardından sütun adlarını göstermek için tablo adını genişletin.</span><span class="sxs-lookup"><span data-stu-id="da743-116">For example, if you are binding to a column value in a dataset's table, expand the name of the dataset, and then expand the table name to display column names.</span></span>

7. <span data-ttu-id="da743-117">Bağlanacak öğenin adına tıklayın.</span><span class="sxs-lookup"><span data-stu-id="da743-117">Click the name of an element to bind to.</span></span>

8. <span data-ttu-id="da743-118">**Biçimlendirme ve Gelişmiş bağlama** iletişim kutusunda çalışıyorsanız, **Özellikler** penceresine dönmek için **Tamam** ' ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="da743-118">If you were working in the **Formatting and Advanced Binding** dialog box, click **OK** to return to the **Properties** window.</span></span>

9. <span data-ttu-id="da743-119">Denetimin ek özelliklerini bağlamak istiyorsanız 3 ile 7 arasındaki adımları yineleyin.</span><span class="sxs-lookup"><span data-stu-id="da743-119">If you want to bind additional properties of the control, repeat steps 3 through 7.</span></span>

    > [!NOTE]
    > <span data-ttu-id="da743-120">Basit-bağlantılı denetimler yalnızca tek bir veri öğesi gösterebildiğinden, basit bağlantılı denetimlerle bir Windows formuna gezinme mantığını eklemek çok normaldir.</span><span class="sxs-lookup"><span data-stu-id="da743-120">Because simple-bound controls show only a single data element, it is very typical to include navigation logic in a Windows Form with simple-bound controls.</span></span>

## <a name="see-also"></a><span data-ttu-id="da743-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="da743-121">See also</span></span>

- <xref:System.Windows.Forms.Binding>
- [<span data-ttu-id="da743-122">Windows Forms Veri Bağlama</span><span class="sxs-lookup"><span data-stu-id="da743-122">Windows Forms Data Binding</span></span>](windows-forms-data-binding.md)
- [<span data-ttu-id="da743-123">Veri Bağlama ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="da743-123">Data Binding and Windows Forms</span></span>](data-binding-and-windows-forms.md)
