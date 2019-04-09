---
title: 'Nasıl yapılır: Bağımlı Veri Dönüştürme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- converting [WPF], bound data
- data binding [WPF], converting bound data
- binding data [WPF], converting bound data
ms.assetid: b00aaa19-c6df-4c3b-a9fd-88a0b488df2b
ms.openlocfilehash: 40699bec1c6cd775f7f8495b7a49eda15fb2ed83
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59093806"
---
# <a name="how-to-convert-bound-data"></a><span data-ttu-id="43849-102">Nasıl yapılır: Bağımlı Veri Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="43849-102">How to: Convert Bound Data</span></span>
<span data-ttu-id="43849-103">Bu örnek uygulama bağlamalarında kullanılan veri dönüştürme işlemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="43849-103">This example shows how to apply conversion to data that is used in bindings.</span></span>  
  
 <span data-ttu-id="43849-104">Veri bağlama sırasında dönüştürmek için uygulayan bir sınıf oluşturmanız <xref:System.Windows.Data.IValueConverter> içeren arabirimi <xref:System.Windows.Data.IValueConverter.Convert%2A> ve <xref:System.Windows.Data.IValueConverter.ConvertBack%2A> yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="43849-104">To convert data during binding, you must create a class that implements the <xref:System.Windows.Data.IValueConverter> interface, which includes the <xref:System.Windows.Data.IValueConverter.Convert%2A> and <xref:System.Windows.Data.IValueConverter.ConvertBack%2A> methods.</span></span>  
  
## <a name="example"></a><span data-ttu-id="43849-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="43849-105">Example</span></span>  
 <span data-ttu-id="43849-106">Aşağıdaki örnekte, yıl, ay ve gün yalnızca gösterir böylece geçilen tarih değeri dönüştürür tarih dönüştürücü uygulanışı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="43849-106">The following example shows the implementation of a date converter that converts the date value passed in so that it only shows the year, the month, and the day.</span></span> <span data-ttu-id="43849-107">Uygularken <xref:System.Windows.Data.IValueConverter> arabirimi, bir uygulama ile donatmak için iyi bir uygulama olan bir <xref:System.Windows.Data.ValueConversionAttribute> geliştirme belirtmek için özniteliği veri türlerini dönüştürme, aşağıdaki örnekte olduğu gibi ilgili araçları:</span><span class="sxs-lookup"><span data-stu-id="43849-107">When implementing the <xref:System.Windows.Data.IValueConverter> interface, it is a good practice to decorate the implementation with a <xref:System.Windows.Data.ValueConversionAttribute> attribute to indicate to development tools the data types involved in the conversion, as in the following example:</span></span>  
  
 [!code-csharp[DataBindingLab#18](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DateConverter.cs#18)]
 [!code-vb[DataBindingLab#18](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/DateConverter.vb#18)]  
  
 <span data-ttu-id="43849-108">Bir dönüştürücü oluşturulduktan sonra bunu bir kaynak olarak ekleyebilirsiniz, [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] dosya.</span><span class="sxs-lookup"><span data-stu-id="43849-108">Once you have created a converter, you can add it as a resource in your [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file.</span></span> <span data-ttu-id="43849-109">Aşağıdaki örnekte, *src* eşler, ad alanına *DateConverter* tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="43849-109">In the following example, *src* maps to the namespace in which *DateConverter* is defined.</span></span>  
  
 [!code-xaml[DataBindingLab#15](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#15)]  
  
 <span data-ttu-id="43849-110">Son olarak, aşağıdaki sözdizimini kullanarak, bağlama dönüştürücüyü kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="43849-110">Finally, you can use the converter in your binding using the following syntax.</span></span> <span data-ttu-id="43849-111">Aşağıdaki örnekte, metin içeriği <xref:System.Windows.Controls.TextBlock> bağlı *StartDate*, bir dış veri kaynağının bir özelliği olan.</span><span class="sxs-lookup"><span data-stu-id="43849-111">In the following example, the text content of the <xref:System.Windows.Controls.TextBlock> is bound to *StartDate*, which is a property of an external data source.</span></span>  
  
 [!code-xaml[DataBindingLab#17](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#17)]  
  
 <span data-ttu-id="43849-112">Yukarıdaki örnekte başvurulan stil kaynakları, bu konuda gösterilen olmayan bir kaynak bölümünde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="43849-112">The style resources referenced in the above example are defined in a resource section not shown in this topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43849-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="43849-113">See also</span></span>

- [<span data-ttu-id="43849-114">Bağlama Doğrulaması Uygulama</span><span class="sxs-lookup"><span data-stu-id="43849-114">Implement Binding Validation</span></span>](how-to-implement-binding-validation.md)
- [<span data-ttu-id="43849-115">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="43849-115">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="43849-116">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="43849-116">How-to Topics</span></span>](data-binding-how-to-topics.md)
