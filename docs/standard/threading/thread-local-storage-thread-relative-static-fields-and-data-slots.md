---
title: 'İş Parçacığında Yerel Depolama: İş Parçacığı Göreli Statik Alanları ve Veri Yuvaları'
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], local storage
- threading [.NET Framework], thread-relative static fields
- local thread storage
- TLS
ms.assetid: c633a4dc-a790-4ed1-96b5-f72bd968b284
ms.openlocfilehash: b5a7c4b78f8599f64aa11f1c98c033866e582933
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73127518"
---
# <a name="thread-local-storage-thread-relative-static-fields-and-data-slots"></a>İş Parçacığında Yerel Depolama: İş Parçacığı Göreli Statik Alanları ve Veri Yuvaları
İş parçacığı ve uygulama etki alanına özgü verileri depolamak için yönetilen iş parçacığı yerel depolama (TLS) kullanabilirsiniz. .NET Framework yönetilen TLS'yi kullanmanın iki yolunu sağlar: iş parçacığına göreli statik alanlar ve veri yuvaları.  
  
- Derleme zamanında tam ihtiyaçlarınızı tahmin `Shared` edebilirseniz iş parçacığı göreli statik alanları (Visual Basic'te iş parçacığı göreli alanlar) kullanın. İş parçacığı göreli statik alanlar en iyi performansı sağlar. Ayrıca derleme zaman türü kontrol yararları verir.  
  
- Gerçek gereksinimleriniz yalnızca çalışma zamanında bulunabilecekolduğunda veri yuvalarını kullanın. Veri yuvaları iş parçacığı göreli statik alanlara göre daha yavaş ve kullanımı <xref:System.Object>daha garip ve veri türü olarak depolanır, bu yüzden kullanmadan önce doğru türe döküm gerekir.  
  
 Yönetilmeyen C++'da, `TlsAlloc` yuvaları dinamik olarak ayırmak `__declspec(thread)` ve iş parçacığı göreli depolamaalanında bir değişkenin ayrılması gerektiğini bildirmek için kullanırsınız. İş parçacığı göreli statik alanlar ve veri yuvaları bu davranışın yönetilen sürümünü sağlar.  
  
 .NET Framework 4'te, nesne <xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType> ilk tüketildiğinde lazily olarak başharfe basılan iş parçacığı yerel nesneleri oluşturmak için sınıfı kullanabilirsiniz. Daha fazla bilgi [için, Lazy Initialization](../../../docs/framework/performance/lazy-initialization.md)bakın.  
  
## <a name="uniqueness-of-data-in-managed-tls"></a>Yönetilen TLS'de Verilerin Benzersizliği  
 İş parçacığına göreli statik alanlar veya veri yuvaları kullanın, yönetilen TLS'deki veriler iş parçacığı ve uygulama etki alanının birleşimine özgüdür.  
  
- Bir uygulama etki alanında, her iki iş parçacığı da aynı alanı veya yuvayı kullansa bile, bir iş parçacığı başka bir iş parçacığından verileri değiştiremez.  
  
- Bir iş parçacığı aynı alana veya birden çok uygulama etki alanından yuvaya erişirken, her uygulama etki alanında ayrı bir değer korunur.  
  
 Örneğin, bir iş parçacığı iş parçacığı göreli statik alanın değerini ayarlar, başka bir uygulama etki alanı girer ve sonra alanın değerini alır, ikinci uygulama etki alanında alınan değer ilk uygulama etki alanındaki değerden farklıdır. İkinci uygulama etki alanında alan için yeni bir değer ayarlamak, alanın ilk uygulama etki alanındaki değerini etkilemez.  
  
 Benzer şekilde, bir iş parçacığı iki farklı uygulama etki alanında aynı adlandırılmış veri yuvası aldığında, ilk uygulama etki alanında veri ikinci uygulama etki alanında veri bağımsız kalır.  
  
## <a name="thread-relative-static-fields"></a>İş Parçacığı-Göreli Statik Alanlar  
 Bir veri parçasının her zaman bir iş parçacığı ve uygulama etki <xref:System.ThreadStaticAttribute> alanı birleşimine özgü olduğunu biliyorsanız, özniteliği statik alana uygulayın. Alanı, diğer statik alanı kullandığınız gibi kullanın. Alandaki veriler, onu kullanan her iş parçacığına özgüdür.  
  
 İş parçacığı göreli statik alanlar veri yuvalarından daha iyi performans sağlar ve derleme zamanı türü denetiminden yararlanır.  
  
 Herhangi bir sınıf oluşturucu kodunun alana erişen ilk bağlamda ki ilk iş parçacığıüzerinde çalışacağından haberdar olun. Aynı uygulama etki alanındaki diğer tüm iş parçacıklarında veya bağlamlarda, alan , başvuru türleri yse `null` (Visual`Nothing` Basic'te) veya değer türleri yse varsayılan değerlerine başolarak başolarak verilir. Bu nedenle, iş parçacığı göreli statik alanları başlatmayı sınıf oluşturucular güvenmemelisiniz. Bunun yerine, iş parçacığı göreli statik alanları başlatmayı `null` `Nothing`kaçının ve bunların () veya varsayılan değerlerine başharflere geçirildiklerini varsayalım.  
  
## <a name="data-slots"></a>Veri Yuvaları  
 .NET Framework iş parçacığı ve uygulama-etki alanı bir arada benzersiz dinamik veri yuvaları sağlar. İki tür veri yuvası vardır: adlandırılmış yuvalar ve adsız yuvalar. Her ikisi de <xref:System.LocalDataStoreSlot> yapı kullanılarak uygulanır.  
  
- Adlandırılmış bir veri yuvası oluşturmak <xref:System.Threading.Thread.AllocateNamedDataSlot%2A?displayProperty=nameWithType> <xref:System.Threading.Thread.GetNamedDataSlot%2A?displayProperty=nameWithType> için, veya yöntemi kullanın. Varolan bir yuvaya başvuru almak için, adını <xref:System.Threading.Thread.GetNamedDataSlot%2A> yönteme geçirin.  
  
- Adsız veri yuvası oluşturmak için <xref:System.Threading.Thread.AllocateDataSlot%2A?displayProperty=nameWithType> yöntemi kullanın.  
  
 Hem adlandırılmış hem de adı <xref:System.Threading.Thread.SetData%2A?displayProperty=nameWithType> <xref:System.Threading.Thread.GetData%2A?displayProperty=nameWithType> açıklanmayan yuvalar için, yuvadaki bilgileri ayarlamak ve almak için yöntemleri kullanın. Bunlar, her zaman bunları yürüten iş parçacığı için veri üzerinde hareket statik yöntemlerdir.  
  
 Adlandırılmış yuvalar uygun olabilir, çünkü adı açıklanmayan bir yuvaya başvuru <xref:System.Threading.Thread.GetNamedDataSlot%2A> tutmak yerine, adını yönteme geçirerek gerektiğinde yuvayı alabilirsiniz. Ancak, iş parçacığı göreli depolama için aynı adı başka bir bileşen kullanır ve bir iş parçacığı hem bileşeninizden hem de diğer bileşenden kod yürütürse, iki bileşen birbirinin verilerini bozabilir. (Bu senaryo, her iki bileşenin de aynı uygulama etki alanında çalıştığını ve aynı verileri paylaşmak üzere tasarlanmadıklarını varsayar.)  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ContextStaticAttribute>
- <xref:System.Threading.Thread.GetNamedDataSlot%2A?displayProperty=nameWithType>
- <xref:System.ThreadStaticAttribute>
- <xref:System.Runtime.Remoting.Messaging.CallContext>
- [İş Parçacığı Oluşturma](../../../docs/standard/threading/index.md)
