---
title: "Nasıl yapılır: Uygulama Hareketlerini Tanıma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application gestures [WPF], recognizing
- gestures [WPF], recognizing
ms.assetid: d58b740f-5192-4a3e-af59-7aa162e6ca15
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 24d9e4435362f5f87185d04f911caf76517a0de9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-recognize-application-gestures"></a><span data-ttu-id="d95eb-102">Nasıl yapılır: Uygulama Hareketlerini Tanıma</span><span class="sxs-lookup"><span data-stu-id="d95eb-102">How To: Recognize Application Gestures</span></span>
<span data-ttu-id="d95eb-103">Aşağıdaki örnek, bir kullanıcı bulunduğunda mürekkep silmek gösterilmiştir bir <xref:System.Windows.Ink.ApplicationGesture.ScratchOut> üzerinde hareket bir <xref:System.Windows.Controls.InkCanvas>.</span><span class="sxs-lookup"><span data-stu-id="d95eb-103">The following example demonstrates how to erase ink when a user makes a <xref:System.Windows.Ink.ApplicationGesture.ScratchOut> gesture on an <xref:System.Windows.Controls.InkCanvas>.</span></span> <span data-ttu-id="d95eb-104">Bu örnek varsayar bir <xref:System.Windows.Controls.InkCanvas>adlı `inkCanvas1`, XAML dosyasında bildirildi.</span><span class="sxs-lookup"><span data-stu-id="d95eb-104">This example assumes an <xref:System.Windows.Controls.InkCanvas>, called `inkCanvas1`, is declared in the XAML file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d95eb-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="d95eb-105">Example</span></span>  
 [!code-csharp[HowToRecognizeGestures#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToRecognizeGestures/CSharp/Window1.xaml.cs#1)]
 [!code-vb[HowToRecognizeGestures#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToRecognizeGestures/VisualBasic/Window1.xaml.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="d95eb-106">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d95eb-106">See Also</span></span>  
 <xref:System.Windows.Ink.ApplicationGesture>  
 <xref:System.Windows.Controls.InkCanvas>  
 <xref:System.Windows.Controls.InkCanvas.Gesture>
