---
title: 'Nasıl yapılır: GroupBox Şablonu Tanımlama'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], GroupBox
- GroupBox control [WPF], creating templates
ms.assetid: 85a4d1a7-4753-4f4a-b26d-14fa10c1ddb5
ms.openlocfilehash: dd53af87ec2d12b2ed0dcf2b23374d76e8f631a9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59225722"
---
# <a name="how-to-define-a-groupbox-template"></a><span data-ttu-id="1983c-102">Nasıl yapılır: GroupBox Şablonu Tanımlama</span><span class="sxs-lookup"><span data-stu-id="1983c-102">How to: Define a GroupBox Template</span></span>
<span data-ttu-id="1983c-103">Bu örnek için bir şablonun nasıl oluşturulacağını gösterir. bir <xref:System.Windows.Controls.GroupBox> denetimi.</span><span class="sxs-lookup"><span data-stu-id="1983c-103">This example shows how to create a template for a <xref:System.Windows.Controls.GroupBox> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1983c-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="1983c-104">Example</span></span>  
 <span data-ttu-id="1983c-105">Aşağıdaki örnekte tanımlayan bir <xref:System.Windows.Controls.GroupBox> denetim şablonu kullanarak bir <xref:System.Windows.Controls.Grid> denetim düzeni için.</span><span class="sxs-lookup"><span data-stu-id="1983c-105">The following example defines a <xref:System.Windows.Controls.GroupBox> control template by using a <xref:System.Windows.Controls.Grid> control for layout.</span></span> <span data-ttu-id="1983c-106">Şablonu kullanan bir <xref:System.Windows.Controls.BorderGapMaskConverter> kenarlığını tanımlamak için <xref:System.Windows.Controls.GroupBox> kenarlık getirmeyecek böylece <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> içeriği.</span><span class="sxs-lookup"><span data-stu-id="1983c-106">The template uses a <xref:System.Windows.Controls.BorderGapMaskConverter> to define the border of the <xref:System.Windows.Controls.GroupBox> so that the border does not obscure the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> content.</span></span>  
  
 [!code-xaml[GroupBoxSnippet#GroupBoxTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#groupboxtemplate)]  
  
## <a name="see-also"></a><span data-ttu-id="1983c-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1983c-107">See also</span></span>

- <xref:System.Windows.Controls.GroupBox>
- <span data-ttu-id="1983c-108">[Nasıl yapılır: Bir grup oluşturun](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms748321(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="1983c-108">[How to: Create a GroupBox](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms748321(v=vs.90))</span></span>
