---
title: ByteStream Kodlayıcı ile İkili Nesneler Kodlama
ms.date: 03/30/2017
ms.assetid: 020ee981-c889-4b12-a3ea-91823ef46444
ms.openlocfilehash: 09a919e11971f81bc76dca0e45a7eb0e70ef749e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64626935"
---
# <a name="encoding-binary-objects-with-bytestream-encoder"></a>ByteStream Kodlayıcı ile İkili Nesneler Kodlama
Gönderme ve alma ham ikili verileri Windows Communication Foundation (WCF) ile yapılandırılmış kullanarak <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement>.  
  
## <a name="byte-stream-message-encoder-architecture"></a>Bayt Stream ileti Kodlayıcı mimarisi  
 WCF tarafından kullanılan ikili ileti Kodlayıcısı, işleme, doğrulama veya iletinin temel alınan ikili veriyi tanımlamak için hiçbir özellik içerir. Veri paketi XML olarak kodlanmış, gönderilen, alınan ve çözülmüş. Kodlayıcı, taşıma ve ileti kuyruğa ileti gönderilmeden önce geçirilen sonra verileri işler. İkili Kodlayıcı ileti verileri işlevsellik, sarmalar `<binary>` öğeleri göndermek ve ileti alındıktan sonra öğeleri kaldırır.  
  
## <a name="using-the-byte-stream-message-encoder"></a>Bayt Stream ileti Kodlayıcı kullanma  
 Aşağıdaki örnek, bayt akışı ileti Kodlayıcı uygulayan bir hizmet sözleşmesini gösterir.  
  
```csharp  
[OperationContract]  
Void Myfunction(Stream stream);  
```  
  
 Aşağıdaki örnek, çağrılan hizmet gösterir.  
  
```csharp  
proxy.MyFunction(stream);  
```  
  
 Bir ileti altyapısı (örneğin, bir yönlendirici) uygulayan bir hizmet kullanarak söz konusu olduğunda, ileti inceleyerek, doğrulama ya da aksi takdirde, iletinin etkileşim olmadan aşağıdaki örnekte gösterildiği gibi işlenir.  
  
```csharp  
[OperationContract]  
void ProcessMessage(Message message) ;  
```  
  
## <a name="scenarios"></a>Senaryolar  
 Bayt Stream Kodlayıcı, aşağıdaki senaryolarda kullanışlıdır.  
  
- Bir JPEG görüntüsünü WCF kullanan bilgisayarlar arasında veri aktarımı. Bu senaryoda, görüntü taşıma bir dış kaynaktan ulaşır ve gönderilen veri görüntüyü oluşturan ham bayt olacaktır. Hizmet ikili verileri almak ve resmi görüntüle.  
  
- Bir ileti kuyruğu dışında bilgileri okunuyor ve işleniyor. İleti bir ileti kuyruğu Yöneticisi'nden okuyun ve işlenecek ileti kuyruğu kanalı geçirildi. İleti kuyruğu kanal WCF kanalı yığındaki bir Kuyruk yöneticisi olarak hareket edecek.  
  
 Bir ileti kuyruğu kanal üzerinden ileti gönderme söz konusu olduğunda, gönderen Kuyruk Yöneticisi'nden alınan bayt miktarı üzerinde denetimi yoktur. Alma işlemi ham bayt okuma yeteneği varsa, iletinin hatalı biçimlendirilmiş ve işlenmeyecek alınır; alma işlemi kullanılabilir bir biçime alınan bayt çevirme özelliğine sahip olacağını varsayılır.
