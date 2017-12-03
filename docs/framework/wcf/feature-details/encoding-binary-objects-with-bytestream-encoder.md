---
title: "ByteStream Kodlayıcı ile İkili Nesneler Kodlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 020ee981-c889-4b12-a3ea-91823ef46444
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d1516731181a7e60445ce19752c3bb1835cb5897
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="encoding-binary-objects-with-bytestream-encoder"></a>ByteStream Kodlayıcı ile İkili Nesneler Kodlama
Ham ikili verileri gönderip [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] kullanılarak yapılandırılmış <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement>.  
  
## <a name="byte-stream-message-encoder-architecture"></a>Bayt akışı ileti Kodlayıcı mimarisi  
 Tarafından kullanılan ikili ileti Kodlayıcı [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] işleme, doğrulama veya iletisi temel ikili verileri tanımlamak için hiçbir özellik içerir. Veri paketi XML kodlanmış, gönderilen, alınan ve kodunu çözdü. Kodlayıcı, taşıma ve ileti kuyruğuna ileti gönderilmeden önce geçirilen sonra verileri işler. İkili kodlama ileti verilerde işlevsellik, sarmalar `<binary>` öğeleri gönderme ve iletiyi aldıktan sonra öğeleri kaldırır.  
  
## <a name="using-the-byte-stream-message-encoder"></a>Bayt akışı ileti Kodlayıcı kullanma  
 Aşağıdaki örnek bayt akışı ileti Kodlayıcı uygulayan bir hizmet sözleşmesini gösterir.  
  
```csharp  
[OperationContract]  
Void Myfunction(Stream stream);  
```  
  
 Aşağıdaki örnek, çağrılan hizmet gösterir.  
  
```csharp  
proxy.MyFunction(stream);  
```  
  
 Bir ileti altyapısı (örneğin, bir yönlendirici) uygulayan bir hizmet kullanarak söz konusu olduğunda, ileti inceleyerek, doğrulama veya aksi halde iletisiyle etkileşim olmadan aşağıdaki örnekte gösterildiği gibi işlenir.  
  
```csharp  
[OperationContract]  
void ProcessMessage(Message message) ;  
```  
  
## <a name="scenarios"></a>Senaryolar  
 Bayt akışı Kodlayıcı aşağıdaki senaryolarda kullanışlıdır.  
  
-   JPEG Resim kullanarak bilgisayarlar arasında veri aktarımı [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Bu senaryoda, görüntü taşıma bir dış kaynaktan ulaşır ve gönderilen veri görüntüyü oluşturan ham bayt olacaktır. Hizmet ikili verileri alır ve resmi görüntüle.  
  
-   Bir ileti sırası bilgilerini okuma ve işleniyor. İleti bir ileti sırası Yöneticisi'nden okuma ve ileti sırası kanalı işlenecek geçirildi. Bir kuyruk Yöneticisi'nde ileti sırası kanal görecek [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kanal yığını.  
  
 İleti sırası kanal üzerinden ileti gönderme söz konusu olduğunda, gönderenin Kuyruk Yöneticisi'nden alınan bayt üzerinde denetimi yoktur. Alma işlemi ham bayt okuma yeteneği varsa, iletinin hatalı biçimlendirilmiş ve işlenmeyecek alınır; alma işlemi alınan bayt kullanılabilir biçime çevirme özelliği olduğunu varsayılır.
