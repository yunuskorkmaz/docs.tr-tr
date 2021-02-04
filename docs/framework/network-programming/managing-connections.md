---
title: Bağlantıları Yönetme
description: Veri kaynakları için HTTP kullanan uygulamaların bağlantıları yönetmek için .NET Framework ServicePoint ve ServicePointManager sınıflarını nasıl kullanabileceği hakkında bilgi edinin.
ms.date: 01/25/2021
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Internet, connections
- HTTP, classes for connecting
- requesting data from Internet, connections
- sending data, connections
- receiving data, connections
- ServicePoint class, about ServicePoint class
- response to Internet request, connections
- connections [.NET Framework], classes
- network resources, connections
- downloading Internet resources, connections
- ServicePointManager class, about ServicePointManager class
ms.assetid: 9b3d3de7-189f-4f7d-81ae-9c29c441aaaa
ms.openlocfilehash: 9ea93c3a9c484fd2a3de58b4d484b1e8445da155
ms.sourcegitcommit: 4df8e005c074ceb1f978f007b222fe253be2baf3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/04/2021
ms.locfileid: "99548064"
---
# <a name="managing-connections"></a>Bağlantıları Yönetme

Veri kaynaklarına bağlanmak için HTTP kullanan uygulamalar, <xref:System.Net.ServicePoint> <xref:System.Net.ServicePointManager> Internet bağlantılarını yönetmek ve en uygun ölçek ve performansa ulaşmak için .NET Framework ve sınıflarını kullanabilir.  

> [!NOTE]
> `ServicePoint` ve `ServicePointManager` .NET Core, .NET 5 ve sonraki sürümlerde eski olarak değerlendirilir. Özelliklerinin ve yöntemlerinin çoğu bu sürümlerde uygulanmaz. Uygulandıklarında, ağ API 'Leri ile ilgili herhangi bir şeyi etkilemez veya izlemez `HttpClient` .
  
 **ServicePoint** sınıfı, uygulamanın Internet kaynaklarına erişim için bağlanabildiği bir uç noktaya sahip bir uygulama sağlar. Her bir **hizmet noktası** , performansı iyileştirmek için bağlantılar arasında iyileştirme bilgilerini paylaşarak bir Internet sunucusuyla bağlantıları iyileştirmeye yardımcı olan bilgileri içerir.  
  
 Her bir **ServicePoint** bir Tekdüzen Kaynak tanımlayıcısı (URI) tarafından tanımlanır ve, URI 'nin şema tanımlayıcısına ve ana bilgisayar parçalara göre kategorize edilir. Örneğin, aynı **ServicePoint** örneği URI 'lere `http://www.contoso.com/index.htm` ve `http://www.contoso.com/news.htm?date=today` aynı düzen tanımlayıcısına (http) ve ana bilgisayar parçalara () sahip olduklarından istek sağlar `www.contoso.com` . Uygulamanın zaten sunucuya kalıcı bağlantısı varsa `www.contoso.com` , her iki isteği de almak için bu bağlantıyı kullanır ve iki bağlantı oluşturma gereksinimini ortadan önler.  
  
 **ServicePointManager** , **ServicePoint** örneklerinin oluşturulmasını ve yok edilmesini yöneten statik bir sınıftır. **ServicePointManager** , uygulama mevcut **ServicePoint** örnekleri koleksiyonunda olmayan bir Internet kaynağı istediğinde bir **ServicePoint** oluşturur. **ServicePoint** örnekleri, maksimum boşta kalma süresini aştığında veya var olan **ServicePoint** örneklerinin sayısı, uygulama Için en fazla **ServicePoint** örneği sayısını aşarsa yok edilir.  <xref:System.Net.ServicePointManager.MaxServicePointIdleTime%2A> <xref:System.Net.ServicePointManager.MaxServicePoints%2A> **ServicePointManager**'daki ve özelliklerini ayarlayarak hem varsayılan en fazla boş süreyi hem de en fazla ServicePoint örneği sayısını denetleyebilirsiniz.  
  
 İstemci ve sunucu arasındaki bağlantı sayısı, uygulama aktarım hızı üzerinde çarpıcı bir etkiye sahip olabilir. Varsayılan olarak, sınıfı kullanan bir uygulama, <xref:System.Net.HttpWebRequest> belirli bir sunucuya en fazla iki kalıcı bağlantı kullanır, ancak en fazla bağlantı sayısını uygulama başına temelinde ayarlayabilirsiniz.  
  
> [!NOTE]
> HTTP/1.1 belirtimi, bir uygulamadaki bağlantı sayısını sunucu başına iki bağlantı ile sınırlandırır.  
  
 En iyi bağlantı sayısı, uygulamanın çalıştığı gerçek koşullara bağlıdır. Uygulamanın kullanabildiği bağlantı sayısını artırmak uygulama performansını etkilemeyebilir. Daha fazla bağlantının etkisini öğrenmek için, bağlantı sayısını değiştirerek performans testlerini çalıştırın. <xref:System.Net.ServicePointManager.DefaultConnectionLimit%2A>Aşağıdaki kod örneğinde gösterildiği gibi, uygulamanın başlatılmasında **ServicePointManager** sınıfında statik özelliğini değiştirerek uygulamanın kullandığı bağlantı sayısını değiştirebilirsiniz.  
  
```csharp  
// Set the maximum number of connections per server to 4.  
ServicePointManager.DefaultConnectionLimit = 4;  
```  
  
```vb  
' Set the maximum number of connections per server to 4.  
ServicePointManager.DefaultConnectionLimit = 4  
```  
  
 **ServicePointManager. DefaultConnectionLimit** özelliğinin değiştirilmesi, daha önce başlatılmış olan **ServicePoint** örneklerini etkilemez. Aşağıdaki kod, sunucu için var olan bir **hizmet noktasındaki** bağlantı sınırının `http://www.contoso.com` ' de depolanan değere değiştirilmesini gösterir `newLimit` .  
  
```csharp  
Uri uri = new Uri("http://www.contoso.com/");  
ServicePoint sp = ServicePointManager.FindServicePoint(uri);  
sp.ConnectionLimit = newLimit;  
```  
  
```vb  
Dim uri As New Uri("http://www.contoso.com/")  
Dim sp As ServicePoint = ServicePointManager.FindServicePoint(uri)  
sp.ConnectionLimit = newLimit  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bağlantı Gruplandırma](connection-grouping.md)
- [Uygulama Protokolleri Kullanma](using-application-protocols.md)
