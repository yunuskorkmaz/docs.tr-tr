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
ms.openlocfilehash: f9ad390626092d481bf47f017f643a29302c1b29
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458862"
---
# <a name="how-to-convert-bound-data"></a><span data-ttu-id="e7748-102">Nasıl yapılır: Bağımlı Veri Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="e7748-102">How to: Convert Bound Data</span></span>
<span data-ttu-id="e7748-103">Bu örnek, bağlamalarda kullanılan verilere dönüştürmenin nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e7748-103">This example shows how to apply conversion to data that is used in bindings.</span></span>  
  
 <span data-ttu-id="e7748-104">Bağlama sırasında verileri dönüştürmek için, <xref:System.Windows.Data.IValueConverter.Convert%2A> ve <xref:System.Windows.Data.IValueConverter.ConvertBack%2A> yöntemlerini içeren <xref:System.Windows.Data.IValueConverter> arabirimini uygulayan bir sınıf oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e7748-104">To convert data during binding, you must create a class that implements the <xref:System.Windows.Data.IValueConverter> interface, which includes the <xref:System.Windows.Data.IValueConverter.Convert%2A> and <xref:System.Windows.Data.IValueConverter.ConvertBack%2A> methods.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7748-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="e7748-105">Example</span></span>  
 <span data-ttu-id="e7748-106">Aşağıdaki örnek, yalnızca yılı, ayı ve günü görüntüleyecek şekilde geçirilen tarih değerini dönüştüren bir tarih dönüştürücünün uygulamasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e7748-106">The following example shows the implementation of a date converter that converts the date value passed in so that it only shows the year, the month, and the day.</span></span> <span data-ttu-id="e7748-107"><xref:System.Windows.Data.IValueConverter> arabirimini uygularken, aşağıdaki örnekte olduğu gibi, dönüştürme işleminde yer alan veri türleri için geliştirme araçlarına işaret eden bir <xref:System.Windows.Data.ValueConversionAttribute> özniteliğiyle uygulamayı süslemek iyi bir uygulamadır:</span><span class="sxs-lookup"><span data-stu-id="e7748-107">When implementing the <xref:System.Windows.Data.IValueConverter> interface, it is a good practice to decorate the implementation with a <xref:System.Windows.Data.ValueConversionAttribute> attribute to indicate to development tools the data types involved in the conversion, as in the following example:</span></span>  
  
 [!code-csharp[DataBindingLab#18](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DateConverter.cs#18)]
 [!code-vb[DataBindingLab#18](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/DateConverter.vb#18)]  
  
 <span data-ttu-id="e7748-108">Dönüştürücüyü oluşturduktan sonra, [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] dosyanıza kaynak olarak ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e7748-108">Once you have created a converter, you can add it as a resource in your [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file.</span></span> <span data-ttu-id="e7748-109">Aşağıdaki örnekte, *src* , *DateConverter* 'ın tanımlandığı ad alanı ile eşlenir.</span><span class="sxs-lookup"><span data-stu-id="e7748-109">In the following example, *src* maps to the namespace in which *DateConverter* is defined.</span></span>  
  
 [!code-xaml[DataBindingLab#15](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#15)]  
  
 <span data-ttu-id="e7748-110">Son olarak, aşağıdaki sözdizimini kullanarak bağlamadaki dönüştürücüyü kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e7748-110">Finally, you can use the converter in your binding using the following syntax.</span></span> <span data-ttu-id="e7748-111">Aşağıdaki örnekte <xref:System.Windows.Controls.TextBlock> metin içeriği, bir dış veri kaynağının özelliği olan *StartDate*' e bağlanır.</span><span class="sxs-lookup"><span data-stu-id="e7748-111">In the following example, the text content of the <xref:System.Windows.Controls.TextBlock> is bound to *StartDate*, which is a property of an external data source.</span></span>  
  
 [!code-xaml[DataBindingLab#17](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#17)]  
  
 <span data-ttu-id="e7748-112">Yukarıdaki örnekte başvurulan stil kaynakları, bu konuda görünmeyen bir kaynak bölümünde tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="e7748-112">The style resources referenced in the above example are defined in a resource section not shown in this topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7748-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e7748-113">See also</span></span>

- [<span data-ttu-id="e7748-114">Bağlama Doğrulaması Uygulama</span><span class="sxs-lookup"><span data-stu-id="e7748-114">Implement Binding Validation</span></span>](how-to-implement-binding-validation.md)
- [<span data-ttu-id="e7748-115">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e7748-115">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="e7748-116">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="e7748-116">How-to Topics</span></span>](data-binding-how-to-topics.md)
