---
title: "Nasıl yapılır: Yazdırma Kuyruklarının Alt Kümesini Numaralandırma"
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
- cpp
helpviewer_keywords:
- enumerating [WPF], subset of print queues
- print queues [WPF], enumerating subset of
ms.assetid: cc4a1b5b-d46f-4c5e-bc26-22c226e4bee0
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 393d1692526551b1eb9aa16f48d3c78c3cd6692f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-enumerate-a-subset-of-print-queues"></a>Nasıl yapılır: Yazdırma Kuyruklarının Alt Kümesini Numaralandırma
Yazıcılar şirket çapında kümesi yönetme bilgi teknolojisi (BT) uzmanları tarafından karşılaşılan yaygın bir durum, belirli özelliklere sahip yazıcıların listesini oluşturmaktır. Bu işlev tarafından sağlanan <xref:System.Printing.PrintServer.GetPrintQueues%2A> yöntemi bir <xref:System.Printing.PrintServer> nesne ve <xref:System.Printing.EnumeratedPrintQueueTypes> numaralandırması.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kod listelemek istediğimiz yazdırma sıralarını özelliklerini belirtin bayraklar dizisi oluşturarak başlar. Bu örnekte, yazdırma sunucusunda yerel olarak yüklenir ve paylaşılan yazdırma sıralarını arıyoruz. <xref:System.Printing.EnumeratedPrintQueueTypes> Numaralandırması pek çok olasılığı sağlar.  
  
 Kod sonra oluşturur bir <xref:System.Printing.LocalPrintServer> nesnesi, türetilmiş bir sınıf <xref:System.Printing.PrintServer>. Yerel yazdırma sunucusuna uygulama çalıştıran bilgisayardır.  
  
 Son önemli adım diziye geçirmektir <xref:System.Printing.PrintServer.GetPrintQueues%2A> yöntemi.  
  
 Son olarak, sonuçların kullanıcıya sunulur.  
  
 [!code-cpp[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](../../../../samples/snippets/cpp/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/CPP/Program.cpp#listsubsetofprintqueues)]
 [!code-csharp[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/CSharp/Program.cs#listsubsetofprintqueues)]
 [!code-vb[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/visualbasic/program.vb#listsubsetofprintqueues)]  
  
 Bu örnek sağlayarak genişletebilirsiniz `foreach` her bir yazdırma sırası daha da incelemek döngü filtreleme. Örneğin, iki taraflı yazdırma döngüyle çağırarak desteklemeyen yazıcıları her yazdırma sırasının ekran <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> yöntemi ve çift yönlü baskı varlığını test döndürülen değer.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Printing.PrintServer.GetPrintQueues%2A>  
 <xref:System.Printing.PrintServer>  
 <xref:System.Printing.LocalPrintServer>  
 <xref:System.Printing.EnumeratedPrintQueueTypes>  
 <xref:System.Printing.PrintQueue>  
 <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>  
 [WPF belgeleri](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [Yazdırma genel bakış](../../../../docs/framework/wpf/advanced/printing-overview.md)  
 [Microsoft XPS Belge Yazıcısı](http://go.microsoft.com/fwlink/?LinkId=147319)
