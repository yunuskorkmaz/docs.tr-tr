---
title: 'Nasıl yapılır: ThicknessConverter Nesnesi Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- border thickness [WPF]
- ThicknessConverter objects [WPF]
ms.assetid: 52682194-d7fd-499c-8005-73fcc84e7b2c
ms.openlocfilehash: ebfb8642a01f6d602f4e5ffa58fde6a8ee0b4e1f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59075957"
---
# <a name="how-to-use-a-thicknessconverter-object"></a><span data-ttu-id="7bdc3-102">Nasıl yapılır: ThicknessConverter Nesnesi Kullanma</span><span class="sxs-lookup"><span data-stu-id="7bdc3-102">How to: Use a ThicknessConverter Object</span></span>
## <a name="example"></a><span data-ttu-id="7bdc3-103">Örnek</span><span class="sxs-lookup"><span data-stu-id="7bdc3-103">Example</span></span>  
 <span data-ttu-id="7bdc3-104">Bu örnek, bir örneğini oluşturma işlemi gösterilmektedir <xref:System.Windows.ThicknessConverter> ve kenarlık kalınlığına değiştirmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7bdc3-104">This example shows how to create an instance of <xref:System.Windows.ThicknessConverter> and use it to change the thickness of a border.</span></span>  
  
 <span data-ttu-id="7bdc3-105">Örnek olarak adlandırılan özel bir yöntem tanımlar `changeThickness`; bu yöntem ilk içeriğini dönüştürür bir <xref:System.Windows.Controls.ListBoxItem>, ayrı bir tanımlandığı şekilde [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] dosyasına bir örneğini <xref:System.Windows.Thickness>ve daha sonra da içerik bilgisini dönüştüren bir <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="7bdc3-105">The example defines a custom method called `changeThickness`; this method first converts the contents of a <xref:System.Windows.Controls.ListBoxItem>, as defined in a separate [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file, to an instance of <xref:System.Windows.Thickness>, and later converts the content into a <xref:System.String>.</span></span> <span data-ttu-id="7bdc3-106">Bu yöntem geçirir <xref:System.Windows.Controls.ListBoxItem> için bir <xref:System.Windows.ThicknessConverter> dönüştüren nesne <xref:System.Windows.Controls.ContentControl.Content%2A> , bir <xref:System.Windows.Controls.ListBoxItem> örneğine <xref:System.Windows.Thickness>.</span><span class="sxs-lookup"><span data-stu-id="7bdc3-106">This method passes the <xref:System.Windows.Controls.ListBoxItem> to a <xref:System.Windows.ThicknessConverter> object, which converts the <xref:System.Windows.Controls.ContentControl.Content%2A> of a <xref:System.Windows.Controls.ListBoxItem> to an instance of <xref:System.Windows.Thickness>.</span></span> <span data-ttu-id="7bdc3-107">Bu değer daha sonra geri değeri olarak geçirilir <xref:System.Windows.Controls.Border.BorderThickness%2A> özelliği <xref:System.Windows.Controls.Border>.</span><span class="sxs-lookup"><span data-stu-id="7bdc3-107">This value is then passed back as the value of the <xref:System.Windows.Controls.Border.BorderThickness%2A> property of the <xref:System.Windows.Controls.Border>.</span></span>  
  
 <span data-ttu-id="7bdc3-108">Bu örnek çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="7bdc3-108">This example does not run.</span></span>  
  
 [!code-csharp[ThicknessConverter#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ThicknessConverter/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ThicknessConverter#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThicknessConverter/VisualBasic/Window1.xaml.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="7bdc3-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7bdc3-109">See also</span></span>

- <xref:System.Windows.Thickness>
- <xref:System.Windows.ThicknessConverter>
- <xref:System.Windows.Controls.Border>
- <span data-ttu-id="7bdc3-110">[Nasıl yapılır: Margin özelliği değiştirme](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms750561(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="7bdc3-110">[How to: Change the Margin Property](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms750561(v=vs.90))</span></span>
- <span data-ttu-id="7bdc3-111">[Nasıl yapılır: Bir ListBoxItem yeni bir veri türüne dönüştürün](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms749147(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="7bdc3-111">[How to: Convert a ListBoxItem to a new Data Type](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms749147(v=vs.90))</span></span>
- [<span data-ttu-id="7bdc3-112">Panellere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="7bdc3-112">Panels Overview</span></span>](../controls/panels-overview.md)
