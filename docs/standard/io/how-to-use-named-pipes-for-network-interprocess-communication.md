---
title: 'Nasıl yapılır: Ağ İşlemler Arası İletişimi için Adlandırılmış Kanallar Kullanma'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- message-based communication [.NET Framework], named pipes
- named pipes [.NET Framework]
- pipes [.NET Framework]
- multiple connections via named pipes
- network communications [.NET Framework], named pipes
- impersonation [.NET Framework], named pipes
- full duplex communcation [.NET Framework], named pipes
ms.assetid: 4e4d7e64-9f1b-4026-98f7-20488ac7b42b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5cc481c7370a21c56daf9ce2949247e65fa33bda
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47084062"
---
# <a name="how-to-use-named-pipes-for-network-interprocess-communication"></a>Nasıl yapılır: Ağ İşlemler Arası İletişimi için Adlandırılmış Kanallar Kullanma
Adlandırılmış kanallar, bir kanal sunucusu ve bir veya daha fazla kanal istemcisi arasındaki işlemler arası iletişimi sağlar. Bunlar, yerel bir bilgisayarda işlemler arası iletişim sağlayan anonim kanallardan daha fazla işlevsellik sağlar. Adlandırılmış kanallar, bağlantı işlemlerinin uzak sunucularda kendi izin setlerini kullanmasını sağlayan bir ağ ve birden çok sunucu örneği, ileti tabanlı iletişim ve istemci kimliğine bürünme üzerinden tam çift yönlü iletişim sağlar.  
  
 Adlandırılmış kanalları uygulamak için <xref:System.IO.Pipes.NamedPipeServerStream> ve <xref:System.IO.Pipes.NamedPipeClientStream> sınıflarını kullanın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, <xref:System.IO.Pipes.NamedPipeServerStream> sınıfını kullanarak adlandırılmış bir kanalın nasıl oluşturulacağını gösterir. Bu örnekte, sunucu işlemi dört iş parçacığı oluşturur. Her bir iş parçacığı bir istemci bağlantısını kabul edebilir. Daha sonra bağlı istemci işlemi sunucuya bir dosya adı sağlar. Eğer istemci yeterli izinlere sahipse, sunucu işlemi dosyayı açar ve dosya içeriğini istemciye geri gönderir.  
  
 [!code-cpp[System.IO.Pipes.NamedPipeServerStream_ImpersonationSample1#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeServerStream_ImpersonationSample1/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.NamedPipeServerStream_ImpersonationSample1#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeServerStream_ImpersonationSample1/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.NamedPipeServerStream_ImpersonationSample1#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeServerStream_ImpersonationSample1/vb/program.vb#01)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte <xref:System.IO.Pipes.NamedPipeClientStream> sınıfını kullanan istemci işlemi gösterilir. İstemci sunucu işlemine bağlanır ve sunucuya bir dosya adı gönderir. Örnek kimliğe bürünme kullanır, bu nedenle istemci uygulamasını çalıştıran kimliğin dosyaya erişim izni olması gerekir. Ardından sunucu, dosyanın içeriğini istemciye geri gönderir. Dosya içerikleri daha sonra konsolda görüntülenir.  
  
 [!code-csharp[System.IO.Pipes.NamedPipeClientStream_ImpersonationSample1#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeClientStream_ImpersonationSample1/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.NamedPipeClientStream_ImpersonationSample1#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeClientStream_ImpersonationSample1/vb/program.vb#01)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Bu örnekte istemci ve sunucu işlemlerinin aynı bilgisayarda çalışması amaçlanmıştır, bu nedenle <xref:System.IO.Pipes.NamedPipeClientStream> nesnesine sağlanan sunucu adı `"."`'dir. Eğer istemci ve sunucu işlemleri ayrı bilgisayarlarda olsaydı `"."`, sunucu işlemini çalıştıran bilgisayarın ağ adı yerine geçecekti.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Security.Principal.TokenImpersonationLevel>  
- <xref:System.IO.Pipes.NamedPipeServerStream.GetImpersonationUserName%2A>  
- [Kanallar](../../../docs/standard/io/pipe-operations.md)  
- [Nasıl yapılır: Yerel İşlemler Arası İletişim için Anonim Kanallar Kullanma](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md)
