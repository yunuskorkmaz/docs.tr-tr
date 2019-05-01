---
title: 'Nasıl yapılır: Yerel İşlemler Arası İletişim için Anonim Kanallar Kullanma'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- anonymous pipes [.NET Framework]
- parent-child communication [.NET Framework]
- pipes [.NET Framework]
- one-way communication [.NET Framework]
- local computer communication [.NET Framework], pipes
ms.assetid: e7773c77-c646-4a01-8a96-a003d59fc4c9
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 810b29b4abde174e3634a03d5c7b5e0e43de11b8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61947179"
---
# <a name="how-to-use-anonymous-pipes-for-local-interprocess-communication"></a>Nasıl yapılır: Yerel İşlemler Arası İletişim için Anonim Kanallar Kullanma
Anonim kanallar, yerel bir bilgisayarda işlemler arası iletişim sağlar. Adlandırılmış kanallardan daha az işlevsellik sağlarlar, ancak daha az yük gerektirirler. Yerel bir bilgisayarda işlemler arası iletişimi kolaylaştırmak için anonim kanalları kullanabilirsiniz. Bir ağ üzerinden iletişim için anonim kanalları kullanamazsınız.  
  
 Anonim kanalları uygulamak için, <xref:System.IO.Pipes.AnonymousPipeServerStream> ve <xref:System.IO.Pipes.AnonymousPipeClientStream> sınıflarını kullanın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir ana işlemden alt işleme anonim kanalları kullanarak bir dize göndermenin yolunu gösterir. Bu örnek, <xref:System.IO.Pipes.AnonymousPipeServerStream>'in bir <xref:System.IO.Pipes.PipeDirection> değeriyle birlikte ana işlemde bir <xref:System.IO.Pipes.PipeDirection.Out> nesnesi oluşturur. Daha sonra ana işlem, bir <xref:System.IO.Pipes.AnonymousPipeClientStream> nesnesi oluşturmak için bir istemci işleyicisi kullanarak bir alt işlem oluşturur. Alt işlem, <xref:System.IO.Pipes.PipeDirection>'in bir <xref:System.IO.Pipes.PipeDirection.In> değerine sahiptir.  
  
 Ardından ana işlem, alt işleme kullanıcı tarafından sağlanan bir dize gönderir. Dize, alt işlemdeki konsolda görüntülenir.  
  
 Aşağıdaki örnek sunucu işlemini gösterir.  
  
 [!code-cpp[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/vb/program.vb#01)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek istemci işlemini gösterir. Sunucu işlemi istemci işlemini başlatır ve bu işleme bir istemci işleyicisi verir. İstemci kodundan oluşturulan yürütülebilir dosya `pipeClient.exe` olarak adlandırılmalıdır ve sunucu işlemi çalıştırılmadan önce sunucu yürütülebilir dosyası olarak aynı dizine kopyalanmalıdır.  
  
 [!code-cpp[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/vb/program.vb#01)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kanallar](../../../docs/standard/io/pipe-operations.md)
- [Nasıl yapılır: Ağ işlemler arası iletişimi için adlandırılmış kanallar kullanma](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md)
