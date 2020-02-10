---
title: 'Nasıl yapılır: Yazdırma Kuyruklarının Alt Kümesini Numaralandırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- enumerating [WPF], subset of print queues
- print queues [WPF], enumerating subset of
ms.assetid: cc4a1b5b-d46f-4c5e-bc26-22c226e4bee0
ms.openlocfilehash: aae41931f012f6d34fc057fdd6ee9fc9baab6e7b
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094546"
---
# <a name="how-to-enumerate-a-subset-of-print-queues"></a>Nasıl yapılır: Yazdırma Kuyruklarının Alt Kümesini Numaralandırma
Şirket genelinde bir yazıcı kümesini yöneten Bilişim Teknolojileri (BT) uzmanlarının karşılaştığı yaygın bir durum, belirli özelliklere sahip yazıcıların bir listesini oluşturmak. Bu işlevsellik, bir <xref:System.Printing.PrintServer> nesnesinin <xref:System.Printing.PrintServer.GetPrintQueues%2A> yöntemi ve <xref:System.Printing.EnumeratedPrintQueueTypes> numaralandırması tarafından sağlanır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte kod, listelemek istediğimiz yazdırma sıralarının özelliklerini belirten bir bayrak dizisi oluşturarak başlar. Bu örnekte, yazdırma sunucusuna yerel olarak yüklenen ve paylaşılan yazdırma kuyruklarını arıyoruz. <xref:System.Printing.EnumeratedPrintQueueTypes> numaralandırması birçok farklı olasılık sağlar.  
  
 Kod daha sonra, <xref:System.Printing.PrintServer>türetilmiş bir sınıf olan bir <xref:System.Printing.LocalPrintServer> nesnesi oluşturur. Yerel yazdırma sunucusu, uygulamanın çalıştığı bilgisayardır.  
  
 Son önemli adım diziyi <xref:System.Printing.PrintServer.GetPrintQueues%2A> yöntemine geçirmektir.  
  
 Son olarak, sonuçlar kullanıcıya sunulur.  
  
 [!code-cpp[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](~/samples/snippets/cpp/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/CPP/Program.cpp#listsubsetofprintqueues)]
 [!code-csharp[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](~/samples/snippets/csharp/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/CSharp/Program.cs#listsubsetofprintqueues)]
 [!code-vb[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](~/samples/snippets/visualbasic/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/visualbasic/program.vb#listsubsetofprintqueues)]  
  
 Bu örneği, her bir yazdırma kuyruğundaki adımları daha fazla filtreleyerek `foreach` döngüsüne sahip olacak şekilde genişletebilirsiniz. Örneğin, döngüyü her bir yazdırma sırasının <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> yöntemini çağırarak ve çift yönlülüme varlığı için döndürülen değeri test ederek iki taraflı yazdırmayı desteklemeyen yazıcılar izleyebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Printing.PrintServer.GetPrintQueues%2A>
- <xref:System.Printing.PrintServer>
- <xref:System.Printing.LocalPrintServer>
- <xref:System.Printing.EnumeratedPrintQueueTypes>
- <xref:System.Printing.PrintQueue>
- <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>
- [WPF'deki Belgeler](documents-in-wpf.md)
- [Yazdırmaya Genel Bakış](printing-overview.md)
- [Microsoft XPS Belge Yazıcısı](/windows/win32/printdocs/microsoft-xps-document-writer)
