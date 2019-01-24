---
title: 'Nasıl yapılır: GridLengthConverter Nesnesi Oluşturma ve Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Grid control [WPF], creating [WPF], GridLengthConverter objects
ms.assetid: 5ab75911-e36a-4825-80e4-081c57e8e182
ms.openlocfilehash: b5ab15df4aaf5f6c4ba7bc7a4b36cc5e122b1320
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54562068"
---
# <a name="how-to-create-and-use-a-gridlengthconverter-object"></a><span data-ttu-id="a8923-102">Nasıl yapılır: GridLengthConverter Nesnesi Oluşturma ve Kullanma</span><span class="sxs-lookup"><span data-stu-id="a8923-102">How to: Create and Use a GridLengthConverter Object</span></span>
## <a name="example"></a><span data-ttu-id="a8923-103">Örnek</span><span class="sxs-lookup"><span data-stu-id="a8923-103">Example</span></span>  
 <span data-ttu-id="a8923-104">Aşağıdaki örnek, bir örneğini oluşturup kullanacağınızı gösterilmektedir <xref:System.Windows.GridLengthConverter>.</span><span class="sxs-lookup"><span data-stu-id="a8923-104">The following example shows how to create and use an instance of <xref:System.Windows.GridLengthConverter>.</span></span> <span data-ttu-id="a8923-105">Örnek olarak adlandırılan özel bir yöntem tanımlar `changeCol`, hangi geçişleri <xref:System.Windows.Controls.ListBoxItem> için bir <xref:System.Windows.GridLengthConverter> dönüştüren <xref:System.Windows.Controls.ContentControl.Content%2A> , bir <xref:System.Windows.Controls.ListBoxItem> örneğine <xref:System.Windows.GridLength>.</span><span class="sxs-lookup"><span data-stu-id="a8923-105">The example defines a custom method called `changeCol`, which passes the <xref:System.Windows.Controls.ListBoxItem> to a <xref:System.Windows.GridLengthConverter> that converts the <xref:System.Windows.Controls.ContentControl.Content%2A> of a <xref:System.Windows.Controls.ListBoxItem> to an instance of <xref:System.Windows.GridLength>.</span></span> <span data-ttu-id="a8923-106">Dönüştürülen değer daha sonra geri değeri olarak geçirilir <xref:System.Windows.Controls.ColumnDefinition.Width%2A> özelliği <xref:System.Windows.Controls.ColumnDefinition> öğesi.</span><span class="sxs-lookup"><span data-stu-id="a8923-106">The converted value is then passed back as the value of the <xref:System.Windows.Controls.ColumnDefinition.Width%2A> property of the <xref:System.Windows.Controls.ColumnDefinition> element.</span></span>  
  
 <span data-ttu-id="a8923-107">Örnek olarak adlandırılan ikinci özel bir yöntem de tanımlar `changeColVal`.</span><span class="sxs-lookup"><span data-stu-id="a8923-107">The example also defines a second custom method, called `changeColVal`.</span></span> <span data-ttu-id="a8923-108">Bu özel yöntem dönüştürür <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> , bir <xref:System.Windows.Controls.Slider> için bir <xref:System.String> ve değeri tekrar sonra geçişleri <xref:System.Windows.Controls.ColumnDefinition> olarak <xref:System.Windows.Controls.ColumnDefinition.Width%2A> öğe.</span><span class="sxs-lookup"><span data-stu-id="a8923-108">This custom method converts the <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> of a <xref:System.Windows.Controls.Slider> to a <xref:System.String> and then passes that value back to the <xref:System.Windows.Controls.ColumnDefinition> as the <xref:System.Windows.Controls.ColumnDefinition.Width%2A> of the element.</span></span>  
  
 <span data-ttu-id="a8923-109">Unutmayın ayrı bir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] dosya içeriğini tanımlayan bir <xref:System.Windows.Controls.ListBoxItem>.</span><span class="sxs-lookup"><span data-stu-id="a8923-109">Note that a separate [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file defines the contents of a <xref:System.Windows.Controls.ListBoxItem>.</span></span>  
  
 [!code-csharp[gridlengthConverterGrid#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridlengthConverterGrid/CSharp/Window1.xaml.cs#1)]
 [!code-vb[gridlengthConverterGrid#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/gridlengthConverterGrid/VisualBasic/Window1.xaml.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="a8923-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a8923-110">See also</span></span>
- <xref:System.Windows.GridLengthConverter>
- <xref:System.Windows.GridLength>
