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
ms.openlocfilehash: 526305f32280fb75e95538b9014c34c11ed8bffa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33556646"
---
# <a name="how-to-convert-bound-data"></a><span data-ttu-id="07f3e-102">Nasıl yapılır: Bağımlı Veri Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="07f3e-102">How to: Convert Bound Data</span></span>
<span data-ttu-id="07f3e-103">Bu örnek nasıl bağlantılarında kullanılan veri dönüştürme uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="07f3e-103">This example shows how to apply conversion to data that is used in bindings.</span></span>  
  
 <span data-ttu-id="07f3e-104">Veri bağlama sırasında dönüştürmek için uygulayan bir sınıf oluşturun <xref:System.Windows.Data.IValueConverter> içeren arabirimi <xref:System.Windows.Data.IValueConverter.Convert%2A> ve <xref:System.Windows.Data.IValueConverter.ConvertBack%2A> yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="07f3e-104">To convert data during binding, you must create a class that implements the <xref:System.Windows.Data.IValueConverter> interface, which includes the <xref:System.Windows.Data.IValueConverter.Convert%2A> and <xref:System.Windows.Data.IValueConverter.ConvertBack%2A> methods.</span></span>  
  
## <a name="example"></a><span data-ttu-id="07f3e-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="07f3e-105">Example</span></span>  
 <span data-ttu-id="07f3e-106">Aşağıdaki örnek, böylece yalnızca yıl, ay ve gün gösterir geçilen tarih değeri dönüştüren tarih dönüştürücü uygulamasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="07f3e-106">The following example shows the implementation of a date converter that converts the date value passed in so that it only shows the year, the month, and the day.</span></span> <span data-ttu-id="07f3e-107">Uygularken <xref:System.Windows.Data.IValueConverter> arabirimi, bir uygulama ile işaretleme iyi bir uygulama olan bir <xref:System.Windows.Data.ValueConversionAttribute> geliştirme belirtmek için öznitelik araçları aşağıdaki örnekteki gibi dönüştürme dahil edilen veri türleri:</span><span class="sxs-lookup"><span data-stu-id="07f3e-107">When implementing the <xref:System.Windows.Data.IValueConverter> interface, it is a good practice to decorate the implementation with a <xref:System.Windows.Data.ValueConversionAttribute> attribute to indicate to development tools the data types involved in the conversion, as in the following example:</span></span>  
  
 [!code-csharp[DataBindingLab#18](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DateConverter.cs#18)]
 [!code-vb[DataBindingLab#18](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/DateConverter.vb#18)]  
  
 <span data-ttu-id="07f3e-108">Bir dönüştürücü oluşturduktan sonra onu bir kaynak olarak ekleyebilirsiniz, [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] dosya.</span><span class="sxs-lookup"><span data-stu-id="07f3e-108">Once you have created a converter, you can add it as a resource in your [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file.</span></span> <span data-ttu-id="07f3e-109">Aşağıdaki örnekte, *src* eşler, ad alanına *DateConverter* tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="07f3e-109">In the following example, *src* maps to the namespace in which *DateConverter* is defined.</span></span>  
  
 [!code-xaml[DataBindingLab#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#15)]  
  
 <span data-ttu-id="07f3e-110">Son olarak, aşağıdaki sözdizimini kullanarak, bağlama dönüştürücü kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="07f3e-110">Finally, you can use the converter in your binding using the following syntax.</span></span> <span data-ttu-id="07f3e-111">Aşağıdaki örnekte, metin içeriği <xref:System.Windows.Controls.TextBlock> bağlı *StartDate*, dış veri kaynağına özelliğinin olduğu.</span><span class="sxs-lookup"><span data-stu-id="07f3e-111">In the following example, the text content of the <xref:System.Windows.Controls.TextBlock> is bound to *StartDate*, which is a property of an external data source.</span></span>  
  
 [!code-xaml[DataBindingLab#17](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#17)]  
  
 <span data-ttu-id="07f3e-112">Yukarıdaki örnekte başvurulan stil kaynakları, bu konuda gösterilmeyen kaynak bölümünde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="07f3e-112">The style resources referenced in the above example are defined in a resource section not shown in this topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07f3e-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="07f3e-113">See Also</span></span>  
 [<span data-ttu-id="07f3e-114">Bağlama Doğrulaması Uygulama</span><span class="sxs-lookup"><span data-stu-id="07f3e-114">Implement Binding Validation</span></span>](../../../../docs/framework/wpf/data/how-to-implement-binding-validation.md)  
 [<span data-ttu-id="07f3e-115">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="07f3e-115">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="07f3e-116">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="07f3e-116">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
