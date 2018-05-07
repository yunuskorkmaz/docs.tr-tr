---
title: ByteStream Kodlayıcı ile İkili Nesneler Kodlama
ms.date: 03/30/2017
ms.assetid: 020ee981-c889-4b12-a3ea-91823ef46444
ms.openlocfilehash: 9619fdf6979833c30159e1ea02b3f8d6b98a6629
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="encoding-binary-objects-with-bytestream-encoder"></a>ByteStream Kodlayıcı ile İkili Nesneler Kodlama
Ham ikili veri Windows Communication Foundation (WCF) ile gönderme ve alma yapılandırılmış kullanarak <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement>.  
  
## <a name="byte-stream-message-encoder-architecture"></a>Bayt akışı ileti Kodlayıcı mimarisi  
 WCF tarafından kullanılan ikili ileti Kodlayıcı işleme, doğrulama veya iletisi temel ikili verileri tanımlamak için hiçbir özellik içerir. Veri paketi XML kodlanmış, gönderilen, alınan ve kodunu çözdü. Kodlayıcı, taşıma ve ileti kuyruğuna ileti gönderilmeden önce geçirilen sonra verileri işler. İkili kodlama ileti verilerde işlevsellik, sarmalar `<binary>` öğeleri gönderme ve iletiyi aldıktan sonra öğeleri kaldırır.  
  
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
  
-   JPEG Resim WCF kullanan bilgisayarlar arasında aktarılıyor. Bu senaryoda, görüntü taşıma bir dış kaynaktan ulaşır ve gönderilen veri görüntüyü oluşturan ham bayt olacaktır. Hizmet ikili verileri alır ve resmi görüntüle.  
  
-   Bir ileti sırası bilgilerini okuma ve işleniyor. İleti bir ileti sırası Yöneticisi'nden okuma ve ileti sırası kanalı işlenecek geçirildi. İleti sırası kanal WCF kanalı yığınında sıra yöneticisi olarak hareket eder.  
  
 İleti sırası kanal üzerinden ileti gönderme söz konusu olduğunda, gönderenin Kuyruk Yöneticisi'nden alınan bayt üzerinde denetimi yoktur. Alma işlemi ham bayt okuma yeteneği varsa, iletinin hatalı biçimlendirilmiş ve işlenmeyecek alınır; alma işlemi alınan bayt kullanılabilir biçime çevirme özelliği olduğunu varsayılır.
