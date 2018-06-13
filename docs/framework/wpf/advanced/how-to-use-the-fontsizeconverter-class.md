---
title: 'Nasıl yapılır: FontSizeConverter Sınıfını Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- FontSizeConverter objects [WPF]
- typography [WPF], FontSizeConverter objects
ms.assetid: 3b0592bd-7223-4860-a108-a5d72f3a9178
ms.openlocfilehash: 625beb06b526e2753abc6f982cf5834bfae1f202
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545132"
---
# <a name="how-to-use-the-fontsizeconverter-class"></a><span data-ttu-id="a9fc5-102">Nasıl yapılır: FontSizeConverter Sınıfını Kullanma</span><span class="sxs-lookup"><span data-stu-id="a9fc5-102">How to: Use the FontSizeConverter Class</span></span>
## <a name="example"></a><span data-ttu-id="a9fc5-103">Örnek</span><span class="sxs-lookup"><span data-stu-id="a9fc5-103">Example</span></span>  
 <span data-ttu-id="a9fc5-104">Bu örnek bir örneğini oluşturmak nasıl gösterir <xref:System.Windows.FontSizeConverter> ve yazı tipi boyutunu değiştirmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a9fc5-104">This example shows how to create an instance of <xref:System.Windows.FontSizeConverter> and use it to change a font size.</span></span>  
  
 <span data-ttu-id="a9fc5-105">Örnek olarak adlandırılan özel bir yöntem tanımlar `changeSize` içeriklerini dönüştürür bir <xref:System.Windows.Controls.ListBoxItem>, ayrı bir tanımlanan [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] dosyasına örneği <xref:System.Double>daha içine bir <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="a9fc5-105">The example defines a custom method called `changeSize` that converts the contents of a <xref:System.Windows.Controls.ListBoxItem>, as defined in a separate [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file, to an instance of <xref:System.Double>, and later into a <xref:System.String>.</span></span> <span data-ttu-id="a9fc5-106">Bu yöntem geçirir <xref:System.Windows.Controls.ListBoxItem> için bir <xref:System.Windows.FontSizeConverter> dönüştürür Nesne <xref:System.Windows.Controls.ContentControl.Content%2A> , bir <xref:System.Windows.Controls.ListBoxItem> örneğine <xref:System.Double>.</span><span class="sxs-lookup"><span data-stu-id="a9fc5-106">This method passes the <xref:System.Windows.Controls.ListBoxItem> to a <xref:System.Windows.FontSizeConverter> object, which converts the <xref:System.Windows.Controls.ContentControl.Content%2A> of a <xref:System.Windows.Controls.ListBoxItem> to an instance of <xref:System.Double>.</span></span> <span data-ttu-id="a9fc5-107">Bu değer daha sonra değeri olarak geri geçirilir <xref:System.Windows.Controls.TextBlock.FontSize%2A> özelliği <xref:System.Windows.Controls.TextBlock> öğesi.</span><span class="sxs-lookup"><span data-stu-id="a9fc5-107">This value is then passed back as the value of the <xref:System.Windows.Controls.TextBlock.FontSize%2A> property of the <xref:System.Windows.Controls.TextBlock> element.</span></span>  
  
 <span data-ttu-id="a9fc5-108">Bu örnek ayrıca adlı ikinci bir özel yöntem tanımlar `changeFamily`.</span><span class="sxs-lookup"><span data-stu-id="a9fc5-108">This example also defines a second custom method that is called `changeFamily`.</span></span> <span data-ttu-id="a9fc5-109">Bu yöntem dönüştürür <xref:System.Windows.Controls.ContentControl.Content%2A> , <xref:System.Windows.Controls.ListBoxItem> için bir <xref:System.String>ve bu değeri geçirir <xref:System.Windows.Controls.TextBlock.FontFamily%2A> özelliği <xref:System.Windows.Controls.TextBlock> öğesi.</span><span class="sxs-lookup"><span data-stu-id="a9fc5-109">This method converts the <xref:System.Windows.Controls.ContentControl.Content%2A> of the <xref:System.Windows.Controls.ListBoxItem> to a <xref:System.String>, and then passes that value to the <xref:System.Windows.Controls.TextBlock.FontFamily%2A> property of the <xref:System.Windows.Controls.TextBlock> element.</span></span>  
  
 <span data-ttu-id="a9fc5-110">Bu örnek çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="a9fc5-110">This example does not run.</span></span>  
  
 [!code-csharp[FontSizeConverter#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSizeConverter/CSharp/Window1.xaml.cs#1)]  
  
## <a name="see-also"></a><span data-ttu-id="a9fc5-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a9fc5-111">See Also</span></span>  
 <xref:System.Windows.FontSizeConverter>
