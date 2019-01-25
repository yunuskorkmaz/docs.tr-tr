---
title: 'Nasıl yapılır: FontSizeConverter Sınıfını Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- FontSizeConverter objects [WPF]
- typography [WPF], FontSizeConverter objects
ms.assetid: 3b0592bd-7223-4860-a108-a5d72f3a9178
ms.openlocfilehash: 7cb76ad4ffe4b4574a48212240b852e1f2253088
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54741905"
---
# <a name="how-to-use-the-fontsizeconverter-class"></a><span data-ttu-id="21b93-102">Nasıl yapılır: FontSizeConverter Sınıfını Kullanma</span><span class="sxs-lookup"><span data-stu-id="21b93-102">How to: Use the FontSizeConverter Class</span></span>
## <a name="example"></a><span data-ttu-id="21b93-103">Örnek</span><span class="sxs-lookup"><span data-stu-id="21b93-103">Example</span></span>  
 <span data-ttu-id="21b93-104">Bu örnek, bir örneğini oluşturma işlemi gösterilmektedir <xref:System.Windows.FontSizeConverter> ve yazı tipi boyutunu değiştirmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="21b93-104">This example shows how to create an instance of <xref:System.Windows.FontSizeConverter> and use it to change a font size.</span></span>  
  
 <span data-ttu-id="21b93-105">Örnek olarak adlandırılan özel bir yöntem tanımlar `changeSize` içeriğini dönüştüren bir <xref:System.Windows.Controls.ListBoxItem>, ayrı bir tanımlandığı şekilde [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] dosyasına örneği <xref:System.Double>daha sonrada bir <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="21b93-105">The example defines a custom method called `changeSize` that converts the contents of a <xref:System.Windows.Controls.ListBoxItem>, as defined in a separate [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file, to an instance of <xref:System.Double>, and later into a <xref:System.String>.</span></span> <span data-ttu-id="21b93-106">Bu yöntem geçirir <xref:System.Windows.Controls.ListBoxItem> için bir <xref:System.Windows.FontSizeConverter> dönüştüren nesne <xref:System.Windows.Controls.ContentControl.Content%2A> , bir <xref:System.Windows.Controls.ListBoxItem> örneğine <xref:System.Double>.</span><span class="sxs-lookup"><span data-stu-id="21b93-106">This method passes the <xref:System.Windows.Controls.ListBoxItem> to a <xref:System.Windows.FontSizeConverter> object, which converts the <xref:System.Windows.Controls.ContentControl.Content%2A> of a <xref:System.Windows.Controls.ListBoxItem> to an instance of <xref:System.Double>.</span></span> <span data-ttu-id="21b93-107">Bu değer daha sonra geri değeri olarak geçirilir <xref:System.Windows.Controls.TextBlock.FontSize%2A> özelliği <xref:System.Windows.Controls.TextBlock> öğesi.</span><span class="sxs-lookup"><span data-stu-id="21b93-107">This value is then passed back as the value of the <xref:System.Windows.Controls.TextBlock.FontSize%2A> property of the <xref:System.Windows.Controls.TextBlock> element.</span></span>  
  
 <span data-ttu-id="21b93-108">Bu örnek ayrıca çağrılan özel bir ikinci yöntem tanımlar `changeFamily`.</span><span class="sxs-lookup"><span data-stu-id="21b93-108">This example also defines a second custom method that is called `changeFamily`.</span></span> <span data-ttu-id="21b93-109">Bu yöntem dönüştürür <xref:System.Windows.Controls.ContentControl.Content%2A> , <xref:System.Windows.Controls.ListBoxItem> için bir <xref:System.String>ve ardından bu değeri geçirir <xref:System.Windows.Controls.TextBlock.FontFamily%2A> özelliği <xref:System.Windows.Controls.TextBlock> öğesi.</span><span class="sxs-lookup"><span data-stu-id="21b93-109">This method converts the <xref:System.Windows.Controls.ContentControl.Content%2A> of the <xref:System.Windows.Controls.ListBoxItem> to a <xref:System.String>, and then passes that value to the <xref:System.Windows.Controls.TextBlock.FontFamily%2A> property of the <xref:System.Windows.Controls.TextBlock> element.</span></span>  
  
 <span data-ttu-id="21b93-110">Bu örnek çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="21b93-110">This example does not run.</span></span>  
  
 [!code-csharp[FontSizeConverter#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSizeConverter/CSharp/Window1.xaml.cs#1)]  
  
## <a name="see-also"></a><span data-ttu-id="21b93-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="21b93-111">See also</span></span>
- <xref:System.Windows.FontSizeConverter>
