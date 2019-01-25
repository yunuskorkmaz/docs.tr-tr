---
title: Bağlantıları yönetme
ms.date: 03/30/2017
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
ms.openlocfilehash: e5579dd05e11de9dd54023604f7515fb52fb29a5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54650739"
---
# <a name="managing-connections"></a>Bağlantıları yönetme
Veri kaynaklarına bağlanmak için HTTP kullanan uygulamalar, .NET Framework'ün kullanabileceğiniz <xref:System.Net.ServicePoint> ve <xref:System.Net.ServicePointManager> sınıfları için Internet bağlantılarını yönetme ve en yüksek ölçek ve performans elde etmelerine yardımcı olmak için.  
  
 **ServicePoint** sınıfı için uygulama bağlanabilir Internet kaynaklarına erişebilmesi için bir uç nokta ile bir uygulama sağlar. Her **ServicePoint** yardımcı performansını artırmak için bağlantıları arasında en iyi duruma getirme bilgilerini paylaşarak bağlantıları Internet sunucusuyla iyileştirme bilgileri içerir.  
  
 Her **ServicePoint** bir Tekdüzen Kaynak Tanımlayıcısı (URI) tarafından tanımlanır ve düzeni tanımlayıcı ve konak parçaları URI göre kategorilere ayrılır. Örneğin, aynı **ServicePoint** örneği istekleri için bir URI'leri sunar `http://www.contoso.com/index.htm` ve `http://www.contoso.com/news.htm?date=today` aynı düzen tanımlayıcısı (http) ve konak parçaları sahip olduğundan (`www.contoso.com`). Uygulama zaten sunucuya kalıcı bir bağlantı varsa `www.contoso.com`, iki bağlantı oluşturmak için gereğinden kurtulursunuz hem istekleri almak için bu bağlantıyı kullanır.  
  
 **ServicePointManager** oluşturma ve yok edilmesini yönetir, statik bir sınıftır **ServicePoint** örnekleri. **ServicePointManager** oluşturur bir **ServicePoint** uygulama koleksiyonunda mevcut olmayan bir Internet kaynağına istediğinde **ServicePoint** örnekleri. **ServicePoint** örnekleri yok, en fazla boşta kalma süresi aştığınızda veya sayısı varolan **ServicePoint** örnekleri üst sınırını aşıyor **ServicePoint**uygulama örnekleri. Varsayılan en fazla boşta kalma süresi hem üst sınırını denetleyebilirsiniz **ServicePoint** ayarlayarak örnekleri <xref:System.Net.ServicePointManager.MaxServicePointIdleTime%2A> ve <xref:System.Net.ServicePointManager.MaxServicePoints%2A> özellikleri **ServicePointManager**.  
  
 İstemci ve sunucu arasındaki bağlantı sayısı, uygulamanın aktarım hızını önemli bir etkisi olabilir. Varsayılan olarak, bir uygulama kullanarak <xref:System.Net.HttpWebRequest> sınıfı iki kalıcı bağlantı verilen bir sunucu için en fazla kullanır, ancak bir uygulama başına temelinde en fazla bağlantı sayısını ayarlayabilirsiniz.  
  
> [!NOTE]
>  HTTP/1.1 belirtimini uygulamadan sunucu başına iki bağlantı için bağlantı sayısını sınırlar.  
  
 En yüksek bağlantı sayısını, uygulamanın çalıştığı gerçek koşullara bağlıdır. Uygulama için kullanılabilir bağlantı sayısının artırılması uygulama performansını etkileyebilir değil. Daha fazla bağlantı etkisini belirlemek için bağlantı sayısını değişen sırasında performans testleri çalıştırın. Statik değiştirerek bir uygulamanın kullandığı bağlantı sayısını değiştirebilirsiniz <xref:System.Net.ServicePointManager.DefaultConnectionLimit%2A> özelliği **ServicePointManager** uygulama başlatma sırasında aşağıdaki kod örneğinde gösterildiği gibi sınıf.  
  
```csharp  
// Set the maximum number of connections per server to 4.  
ServicePointManager.DefaultConnectionLimit = 4;  
```  
  
```vb  
' Set the maximum number of connections per server to 4.  
ServicePointManager.DefaultConnectionLimit = 4  
```  
  
 Değiştirme **ServicePointManager.DefaultConnectionLimit** özelliği daha önce başlatılmış etkilemez **ServicePoint** örnekleri. Aşağıdaki kod, var olan bir bağlantı sınırı değiştirme gösterir **ServicePoint** sunucusunun `http://www.contoso.com` depolanan değere `newLimit`.  
  
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
- [Bağlantı Gruplandırma](../../../docs/framework/network-programming/connection-grouping.md)
- [Uygulama Protokolleri Kullanma](../../../docs/framework/network-programming/using-application-protocols.md)
