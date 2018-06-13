---
title: 'Nasıl yapılır: Uygulama Hareketlerini Tanıma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application gestures [WPF], recognizing
- gestures [WPF], recognizing
ms.assetid: d58b740f-5192-4a3e-af59-7aa162e6ca15
ms.openlocfilehash: 82ca91fc9e3745012d82357991b67f398079f1f7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33543699"
---
# <a name="how-to-recognize-application-gestures"></a><span data-ttu-id="74966-102">Nasıl yapılır: Uygulama Hareketlerini Tanıma</span><span class="sxs-lookup"><span data-stu-id="74966-102">How To: Recognize Application Gestures</span></span>
<span data-ttu-id="74966-103">Aşağıdaki örnek, bir kullanıcı bulunduğunda mürekkep silmek gösterilmiştir bir <xref:System.Windows.Ink.ApplicationGesture.ScratchOut> üzerinde hareket bir <xref:System.Windows.Controls.InkCanvas>.</span><span class="sxs-lookup"><span data-stu-id="74966-103">The following example demonstrates how to erase ink when a user makes a <xref:System.Windows.Ink.ApplicationGesture.ScratchOut> gesture on an <xref:System.Windows.Controls.InkCanvas>.</span></span> <span data-ttu-id="74966-104">Bu örnek varsayar bir <xref:System.Windows.Controls.InkCanvas>adlı `inkCanvas1`, XAML dosyasında bildirildi.</span><span class="sxs-lookup"><span data-stu-id="74966-104">This example assumes an <xref:System.Windows.Controls.InkCanvas>, called `inkCanvas1`, is declared in the XAML file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="74966-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="74966-105">Example</span></span>  
 [!code-csharp[HowToRecognizeGestures#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToRecognizeGestures/CSharp/Window1.xaml.cs#1)]
 [!code-vb[HowToRecognizeGestures#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToRecognizeGestures/VisualBasic/Window1.xaml.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="74966-106">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="74966-106">See Also</span></span>  
 <xref:System.Windows.Ink.ApplicationGesture>  
 <xref:System.Windows.Controls.InkCanvas>  
 <xref:System.Windows.Controls.InkCanvas.Gesture>
