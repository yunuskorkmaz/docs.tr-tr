---
title: 'Nasıl yapılır: GridLengthConverter Nesnesi Oluşturma ve Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Grid control [WPF], creating [WPF], GridLengthConverter objects
ms.assetid: 5ab75911-e36a-4825-80e4-081c57e8e182
ms.openlocfilehash: 498d2b9c531f391f4cbeb1478469a99d381deec7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59206791"
---
# <a name="how-to-create-and-use-a-gridlengthconverter-object"></a><span data-ttu-id="e0580-102">Nasıl yapılır: GridLengthConverter Nesnesi Oluşturma ve Kullanma</span><span class="sxs-lookup"><span data-stu-id="e0580-102">How to: Create and Use a GridLengthConverter Object</span></span>
## <a name="example"></a><span data-ttu-id="e0580-103">Örnek</span><span class="sxs-lookup"><span data-stu-id="e0580-103">Example</span></span>  
 <span data-ttu-id="e0580-104">Aşağıdaki örnek, bir örneğini oluşturup kullanacağınızı gösterilmektedir <xref:System.Windows.GridLengthConverter>.</span><span class="sxs-lookup"><span data-stu-id="e0580-104">The following example shows how to create and use an instance of <xref:System.Windows.GridLengthConverter>.</span></span> <span data-ttu-id="e0580-105">Örnek olarak adlandırılan özel bir yöntem tanımlar `changeCol`, hangi geçişleri <xref:System.Windows.Controls.ListBoxItem> için bir <xref:System.Windows.GridLengthConverter> dönüştüren <xref:System.Windows.Controls.ContentControl.Content%2A> , bir <xref:System.Windows.Controls.ListBoxItem> örneğine <xref:System.Windows.GridLength>.</span><span class="sxs-lookup"><span data-stu-id="e0580-105">The example defines a custom method called `changeCol`, which passes the <xref:System.Windows.Controls.ListBoxItem> to a <xref:System.Windows.GridLengthConverter> that converts the <xref:System.Windows.Controls.ContentControl.Content%2A> of a <xref:System.Windows.Controls.ListBoxItem> to an instance of <xref:System.Windows.GridLength>.</span></span> <span data-ttu-id="e0580-106">Dönüştürülen değer daha sonra geri değeri olarak geçirilir <xref:System.Windows.Controls.ColumnDefinition.Width%2A> özelliği <xref:System.Windows.Controls.ColumnDefinition> öğesi.</span><span class="sxs-lookup"><span data-stu-id="e0580-106">The converted value is then passed back as the value of the <xref:System.Windows.Controls.ColumnDefinition.Width%2A> property of the <xref:System.Windows.Controls.ColumnDefinition> element.</span></span>  
  
 <span data-ttu-id="e0580-107">Örnek olarak adlandırılan ikinci özel bir yöntem de tanımlar `changeColVal`.</span><span class="sxs-lookup"><span data-stu-id="e0580-107">The example also defines a second custom method, called `changeColVal`.</span></span> <span data-ttu-id="e0580-108">Bu özel yöntem dönüştürür <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> , bir <xref:System.Windows.Controls.Slider> için bir <xref:System.String> ve değeri tekrar sonra geçişleri <xref:System.Windows.Controls.ColumnDefinition> olarak <xref:System.Windows.Controls.ColumnDefinition.Width%2A> öğe.</span><span class="sxs-lookup"><span data-stu-id="e0580-108">This custom method converts the <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> of a <xref:System.Windows.Controls.Slider> to a <xref:System.String> and then passes that value back to the <xref:System.Windows.Controls.ColumnDefinition> as the <xref:System.Windows.Controls.ColumnDefinition.Width%2A> of the element.</span></span>  
  
 <span data-ttu-id="e0580-109">Unutmayın ayrı bir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] dosya içeriğini tanımlayan bir <xref:System.Windows.Controls.ListBoxItem>.</span><span class="sxs-lookup"><span data-stu-id="e0580-109">Note that a separate [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file defines the contents of a <xref:System.Windows.Controls.ListBoxItem>.</span></span>  
  
 [!code-csharp[gridlengthConverterGrid#1](~/samples/snippets/csharp/VS_Snippets_Wpf/gridlengthConverterGrid/CSharp/Window1.xaml.cs#1)]
 [!code-vb[gridlengthConverterGrid#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/gridlengthConverterGrid/VisualBasic/Window1.xaml.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="e0580-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e0580-110">See also</span></span>

- <xref:System.Windows.GridLengthConverter>
- <xref:System.Windows.GridLength>
