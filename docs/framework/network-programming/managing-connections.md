---
title: Bağlantıları Yönetme
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
ms.openlocfilehash: 11c17c6893800fce8bbff8f49b3a207c161bcdfa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047642"
---
# <a name="managing-connections"></a>Bağlantıları Yönetme
Veri kaynaklarına bağlanmak için HTTP'yi kullanan uygulamalar, <xref:System.Net.ServicePoint> Internet <xref:System.Net.ServicePointManager> bağlantılarını yönetmek ve optimum ölçek ve performans elde etmelerine yardımcı olmak için .NET Framework'ün ve sınıflarını kullanabilir.  
  
 **ServicePoint** sınıfı, uygulamanın Internet kaynaklarına erişebileceği bir bitiş noktası olan bir uygulama sağlar. Her **ServicePoint,** performansı artırmak için en iyi duruma getirme bilgilerini bağlantılar arasında paylaşarak bir Internet sunucusuyla bağlantıları optimize etmeye yardımcı olan bilgiler içerir.  
  
 Her **ServicePoint,** Tek düzen kaynak tanımlayıcısı (URI) tarafından tanımlanır ve URI'nin şema tanımlayıcısı ve ana bilgisayar parçalarına göre sınıflandırılır. Örneğin, aynı **ServicePoint** örneği, UrI'lere `http://www.contoso.com/index.htm` `http://www.contoso.com/news.htm?date=today` istekler sağlar ve aynı şema tanımlayıcısına (http)`www.contoso.com`ve ana bilgisayar parçalarına ( ) sahip olduklarından. Uygulama zaten sunucuya `www.contoso.com`kalıcı bir bağlantı varsa, iki bağlantı oluşturmak için gerek kaçınarak, her iki isteği almak için bu bağlantıyı kullanır.  
  
 **ServicePointManager,** **ServicePoint** örneklerinin oluşturulmasını ve yok edilmesini yöneten statik bir sınıftır. **ServicePointManager,** uygulama varolan **ServicePoint** örneklerinin koleksiyonunda olmayan bir Internet kaynağı istediğinde bir **ServicePoint** oluşturur. **ServicePoint** örnekleri, maksimum boşta kalma sürelerini aştıklarında veya varolan **ServicePoint** örneklerinin sayısı uygulama için en fazla **ServicePoint** örneği sayısını aştığında yok edilir. **ServicePointManager'daki**özellikleri <xref:System.Net.ServicePointManager.MaxServicePointIdleTime%2A> ve <xref:System.Net.ServicePointManager.MaxServicePoints%2A> özellikleri ayarlayarak hem varsayılan maksimum boşta kalma süresini hem de en fazla **ServicePoint** örneğini denetleyebilirsiniz.  
  
 İstemci ve sunucu arasındaki bağlantı sayısı, uygulama verime üzerinde önemli bir etkiye sahip olabilir. Varsayılan olarak, <xref:System.Net.HttpWebRequest> sınıfı kullanan bir uygulama belirli bir sunucuya en fazla iki kalıcı bağlantı kullanır, ancak uygulama başına en fazla bağlantı sayısını ayarlayabilirsiniz.  
  
> [!NOTE]
> HTTP/1.1 belirtimi, bir uygulamadan bağlantı sayısını sunucu başına iki bağlantıyla sınırlar.  
  
 En uygun bağlantı sayısı, uygulamanın çalıştığı gerçek koşullara bağlıdır. Uygulamaiçin kullanılabilen bağlantı sayısını artırmak uygulama performansını etkilemeyebilir. Daha fazla bağlantının etkisini belirlemek için, bağlantı sayısını değiştirerek performans testleri çalıştırın. Aşağıdaki kod örneğinde gösterildiği gibi, uygulama başlatma <xref:System.Net.ServicePointManager.DefaultConnectionLimit%2A> sırasında **ServicePointManager** sınıfındaki statik özelliği değiştirerek bir uygulamanın kullandığı bağlantı sayısını değiştirebilirsiniz.  
  
```csharp  
// Set the maximum number of connections per server to 4.  
ServicePointManager.DefaultConnectionLimit = 4;  
```  
  
```vb  
' Set the maximum number of connections per server to 4.  
ServicePointManager.DefaultConnectionLimit = 4  
```  
  
 **ServicePointManager.DefaultConnectionLimit** özelliğini değiştirmek, önceden başlatılan **ServicePoint** örneklerini etkilemez. Aşağıdaki kod, sunucunun `http://www.contoso.com` varolan bir `newLimit` **ServicePoint'teki** bağlantı sınırını depolanan değerle değiştirmeyi gösterir.  
  
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
