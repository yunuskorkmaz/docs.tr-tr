---
title: "Nasıl yapılır: GroupBox Şablonu Tanımlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [WPF], GroupBox
- GroupBox control [WPF], creating templates
ms.assetid: 85a4d1a7-4753-4f4a-b26d-14fa10c1ddb5
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6022f4a521fa64246a24b7aab21c368f5f72af8d
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-define-a-groupbox-template"></a><span data-ttu-id="e6b17-102">Nasıl yapılır: GroupBox Şablonu Tanımlama</span><span class="sxs-lookup"><span data-stu-id="e6b17-102">How to: Define a GroupBox Template</span></span>
<span data-ttu-id="e6b17-103">Bu örnek için bir şablon oluşturmak nasıl gösterir bir <xref:System.Windows.Controls.GroupBox> denetim.</span><span class="sxs-lookup"><span data-stu-id="e6b17-103">This example shows how to create a template for a <xref:System.Windows.Controls.GroupBox> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6b17-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="e6b17-104">Example</span></span>  
 <span data-ttu-id="e6b17-105">Aşağıdaki örnek tanımlayan bir <xref:System.Windows.Controls.GroupBox> denetim şablonu kullanarak bir <xref:System.Windows.Controls.Grid> denetim düzeni için.</span><span class="sxs-lookup"><span data-stu-id="e6b17-105">The following example defines a <xref:System.Windows.Controls.GroupBox> control template by using a <xref:System.Windows.Controls.Grid> control for layout.</span></span> <span data-ttu-id="e6b17-106">Şablonu kullanan bir <xref:System.Windows.Controls.BorderGapMaskConverter> kenarlığını tanımlamak için <xref:System.Windows.Controls.GroupBox> kenarlık değil soyutlamaması böylece <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> içeriği.</span><span class="sxs-lookup"><span data-stu-id="e6b17-106">The template uses a <xref:System.Windows.Controls.BorderGapMaskConverter> to define the border of the <xref:System.Windows.Controls.GroupBox> so that the border does not obscure the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> content.</span></span>  
  
 [!code-xaml[GroupBoxSnippet#GroupBoxTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#groupboxtemplate)]  
  
## <a name="see-also"></a><span data-ttu-id="e6b17-107">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e6b17-107">See Also</span></span>  
 <xref:System.Windows.Controls.GroupBox>  
 [<span data-ttu-id="e6b17-108">GroupBox nasıl yapılır konuları</span><span class="sxs-lookup"><span data-stu-id="e6b17-108">GroupBox How-to Topics</span></span>](http://msdn.microsoft.com/library/7692e155-a4c6-428c-b7e0-64b3740daca7)
