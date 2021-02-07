---
description: 'Hakkında daha fazla bilgi edinin: ByteStream kodlayıcı ile Ikili nesneleri kodlama'
title: ByteStream Kodlayıcı ile İkili Nesneler Kodlama
ms.date: 03/30/2017
ms.assetid: 020ee981-c889-4b12-a3ea-91823ef46444
ms.openlocfilehash: 4ef3d3cd378abacd14dd502530a8090f3982e4ea
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99704907"
---
# <a name="encoding-binary-objects-with-bytestream-encoder"></a>ByteStream Kodlayıcı ile İkili Nesneler Kodlama

Windows Communication Foundation (WCF) ile ham ikili verileri gönderme ve alma kullanılarak yapılandırılır <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement> .  
  
## <a name="byte-stream-message-encoder-architecture"></a>Bayt akışı Ileti Kodlayıcısı mimarisi  

 WCF tarafından kullanılan ikili ileti Kodlayıcısı, iletideki temel alınan ikili verileri işlemeye, doğrulamaya veya tanımlamaya yönelik bir özellik içermez. Veri paketi XML olarak kodlanır, gönderilir, alınır ve kodu çözülür. Kodlayıcı, ulaşım 'e geçtikten sonra ve ileti ileti kuyruğuna gönderilmeden önce verileri işler. İşlevsellik, ikili kodlayıcı, ileti `<binary>` alındıktan sonra öğeleri göndermek ve silmek için öğeler halinde ileti verilerini sarmalanmış.  
  
## <a name="using-the-byte-stream-message-encoder"></a>Byte Stream Ileti Kodlayıcısı 'nı kullanma  

 Aşağıdaki örnek, bayt akışı ileti Kodlayıcısı 'nı uygulayan bir hizmet sözleşmesini gösterir.  
  
```csharp  
[OperationContract]  
Void Myfunction(Stream stream);  
```  
  
 Aşağıdaki örnek, çağrılan hizmeti gösterir.  
  
```csharp  
proxy.MyFunction(stream);  
```  
  
 İleti altyapısını uygulayan bir hizmet (örneğin, yönlendirici) kullanıldığında ileti, aşağıdaki örnekte gösterildiği gibi İnceleme, doğrulama veya başka bir şekilde etkileşimde bulunmadan işlenir.  
  
```csharp  
[OperationContract]  
void ProcessMessage(Message message) ;  
```  
  
## <a name="scenarios"></a>Senaryolar  

 Byte Stream Encoder, aşağıdaki senaryolarda faydalıdır.  
  
- WCF kullanarak bir JPEG görüntüsünü bilgisayarlar arasında aktarma. Bu senaryoda, görüntü bir dış kaynaktan aktarımdan geçer ve gönderilen veriler görüntüyü oluşturan ham bayt olur. Bir hizmet ikili verileri alır ve görüntüyü görüntüler.  
  
- Bilgileri bir ileti kuyruğundan okuma ve işleme. İleti bir ileti kuyruğu yöneticisinden okunacak ve işlenmek üzere ileti kuyruğu kanalının başarılı olacağı. İleti kuyruğu kanalı, WCF kanal yığınında bir sıra Yöneticisi görevi görür.  
  
 İleti kuyruğu kanalı üzerinden bir ileti gönderdiğinizde, gönderenin kuyruk yöneticisinden alınan baytlar üzerinde denetimi yoktur. Alıcı işlemin ham baytları okuma yeteneği yoksa, ileti hatalı olarak biçimlendirilir ve işlenmeyecek olur; alma işleminin alınan baytları kullanılabilir bir biçime geri çevirme yeteneğine sahip olacağı varsayılır.
