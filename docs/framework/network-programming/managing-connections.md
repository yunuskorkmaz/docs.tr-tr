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
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 8702f2329b262fc5c5965ae49365d46ba34091d6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33391179"
---
# <a name="managing-connections"></a>Bağlantıları yönetme
Veri kaynaklarına bağlanmak için HTTP kullanan uygulamalar, .NET Framework'ün kullanabileceğiniz <xref:System.Net.ServicePoint> ve <xref:System.Net.ServicePointManager> sınıfları internet bağlantıları yönetmek ve bunları en uygun ölçek ve performans elde etmek amacıyla.  
  
 **ServicePoint** sınıfı, bir uygulama için uygulama bağlanabilir Internet kaynaklarına erişmek için bir uç nokta ile sağlar. Her **ServicePoint** yardımcı performansını artırmak için bağlantıları arasında en iyi duruma getirme bilgilerini paylaşarak bir Internet sunucusu ile bağlantı iyileştirmek bilgileri içerir.  
  
 Her **ServicePoint** bir Tekdüzen Kaynak Tanımlayıcısı (URI) tarafından tanımlanır ve düzeni tanımlayıcısı ve ana bilgisayar parçaları URI'sinin göre kategorilere ayrılmıştır. Örneğin, aynı **ServicePoint** örneği için URI istekleri sağlamak http://www.contoso.com/index.htm ve http://www.contoso.com/news.htm?date=today aynı düzen tanımlayıcısı (http) ve ana bilgisayar parçaları (www.contoso.com) sahip olduğundan. Uygulama zaten sunucu www.contoso.com kalıcı bir bağlantı varsa, iki bağlantı oluşturmak için gereken önleme hem istekleri almak için bu bağlantıyı kullanır.  
  
 **ServicePointManager** oluşturma ve yok etme yöneten statik bir sınıftır **ServicePoint** örnekleri. **ServicePointManager** oluşturur bir **ServicePoint** koleksiyonunda var olmayan bir Internet kaynağına uygulama isteğinde bulunduğunda **ServicePoint** örnekleri. **ServicePoint** örnekleri kendi maksimum boşta kalma süresi aştığınızda veya sayısı yok varolan **ServicePoint** örnekleri üst sınırını aşıyor **ServicePoint**uygulama örneği. Varsayılan en fazla boşta kalma süresi ve en fazla sayısını kontrol edebilirsiniz **ServicePoint** ayarlayarak örnekleri <xref:System.Net.ServicePointManager.MaxServicePointIdleTime%2A> ve <xref:System.Net.ServicePointManager.MaxServicePoints%2A> özellikleri **ServicePointManager**.  
  
 İstemci ve sunucu arasındaki bağlantı sayısı üzerinde uygulama üretilen işi çarpıcı bir etkisi olabilir. Varsayılan olarak, bir uygulama kullanarak <xref:System.Net.HttpWebRequest> sınıfı, belirli bir sunucuda iki kalıcı bağlantı maksimum kullanır, ancak bir uygulama başına temelinde en fazla bağlantı sayısını ayarlayabilirsiniz.  
  
> [!NOTE]
>  HTTP/1.1 belirtimini sunucu başına iki bağlantı uygulamaya bağlantı sayısını sınırlar.  
  
 En yüksek bağlantı sayısını uygulamanın çalıştığı gerçek koşullara bağlıdır. Uygulama için kullanılabilir bağlantı sayısını artırmayı uygulama performansını etkileyebilir değil. Daha fazla bağlantı etkisini belirlemek için bağlantı sayısı değişen sırasında performans testleri çalıştırın. Statik değiştirerek bir uygulamanın kullandığı bağlantı sayısını değiştirebilirsiniz <xref:System.Net.ServicePointManager.DefaultConnectionLimit%2A> özelliği **ServicePointManager** aşağıdaki kod örneğinde gösterildiği gibi uygulama başlatma sırasında sınıfı.  
  
```csharp  
// Set the maximum number of connections per server to 4.  
ServicePointManager.DefaultConnectionLimit = 4;  
```  
  
```vb  
' Set the maximum number of connections per server to 4.  
ServicePointManager.DefaultConnectionLimit = 4  
```  
  
 Değiştirme **ServicePointManager.DefaultConnectionLimit** özelliği daha önce başlatılmış etkilemez **ServicePoint** örnekleri. Aşağıdaki kod, var olan üzerinde bağlantı sınırı değiştirme gösterir **ServicePoint** sunucusu http://www.contoso.com depolanan değerine `newLimit`.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bağlantı Gruplandırma](../../../docs/framework/network-programming/connection-grouping.md)  
 [Uygulama Protokolleri Kullanma](../../../docs/framework/network-programming/using-application-protocols.md)
