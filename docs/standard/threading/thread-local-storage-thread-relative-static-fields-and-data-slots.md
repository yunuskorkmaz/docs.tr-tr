---
title: 'İş parçacığı yerel deposu: İş parçacığı göreli statik alanları ve veri yuvaları'
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], local storage
- threading [.NET Framework], thread-relative static fields
- local thread storage
- TLS
ms.assetid: c633a4dc-a790-4ed1-96b5-f72bd968b284
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 69107cd7f1f84fa402479bb8a76c4b9b8a825d69
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54718266"
---
# <a name="thread-local-storage-thread-relative-static-fields-and-data-slots"></a>İş parçacığı yerel deposu: İş parçacığı göreli statik alanları ve veri yuvaları
Bir iş parçacığı ve uygulama etki alanı için benzersiz olan yönetilen iş parçacığı yerel depolaması (TLS) verileri depolamak için kullanabilirsiniz. .NET Framework yönetilen TLS kullanmak için iki yol sunar: iş parçacığı göreli statik alanları ve veri yuvaları.  
  
-   İş parçacığı göreli statik alanları kullanın (iş parçacığı göreli `Shared` alanları Visual Basic'te) derleme zamanında tam olarak karşılayacak düşünüyorsanız. İş parçacığı göreli statik alanları, en iyi performansı sağlar. Bunlar ayrıca, derleme zamanı tür denetimi avantajlarını sağlar.  
  
-   Yalnızca çalışma zamanında gerçek gereksinimlerinizi fark veri yuvaları kullanın. Veri yuvaları daha yavaş ve daha iş parçacığı göreli statik alanları kullanmak garip ve veri türü olarak depolanan <xref:System.Object>, kullanmadan önce doğru türe dönüştürmeniz gerekir.  
  
 Yönetilmeyen C++'da, kullandığınız `TlsAlloc` yuvaları dinamik olarak ayırabilir ve `__declspec(thread)` iş parçacığı göreli depolama ayrılması gereken bir değişken bildirmek için. İş parçacığı göreli statik alanları ve veri yuvaları bu davranışı yönetilen bir sürümünü sağlayın.  
  
 İçinde [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], kullanabileceğiniz <xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType> nesne ilk kez kullanıldığında, gevşek başlatılır iş parçacığı-yerel nesneleri oluşturmak için sınıf. Daha fazla bilgi için [yavaş başlatma](../../../docs/framework/performance/lazy-initialization.md).  
  
## <a name="uniqueness-of-data-in-managed-tls"></a>Yönetilen TLS veri benzersizliği  
 İş parçacığı göreli statik alanları veya veri yuvaları kullanmanıza bakılmaksızın, iş parçacığı ve uygulama etki alanı birleşimi için yönetilen TLS verilerinde benzersizdir.  
  
-   Her iki iş parçacığının aynı alanı veya yuvası kullandığınızda da bir uygulama etki alanı içinde başka bir iş parçacığından verileri tek bir iş parçacığı değiştiremezsiniz.  
  
-   Bir iş parçacığı aynı alanı veya yuvası birden çok uygulama etki alanından eriştiğinde, ayrı bir değer her uygulama etki alanında tutulur.  
  
 Örneğin, bir iş parçacığı ayarlar iş parçacığı göreli statik alanının değeri başka bir uygulama etki alanına girdiğinden ve alanın değerini alır., ikinci uygulama etki alanında alınan değeri ilk uygulama etki alanı değeri farklılık gösterir. İkinci uygulama etki alanında alan için yeni bir değer ayarlamak alanın değeri ilk uygulama etki alanındaki etkilemez.  
  
 Benzer şekilde, bir iş parçacığı iki farklı uygulama etki alanları aynı adlandırılmış veri yuvaya aldığında, verileri ilk uygulama etki alanında ikinci uygulama etki alanındaki verilerin bağımsız kalır.  
  
## <a name="thread-relative-static-fields"></a>İş parçacığı göreli statik alanları  
 Bir veri parçasını her zaman bir iş parçacığı ve uygulama etki alanı birleşimi benzersiz olduğunu biliyorsanız, uygulama <xref:System.ThreadStaticAttribute> statik alanına öznitelik. Herhangi bir statik alan kullandığınız gibi alanını kullanın. Bu alandaki veri, bunu kullanan her bir iş parçacığı için benzersizdir.  
  
 İş parçacığı göreli statik alanları veri yuvaları daha iyi performans sağlar ve derleme zamanı tür denetimi faydası vardır.  
  
 Herhangi bir sınıf oluşturucu kodu alan erişen ilk bağlamında ilk iş parçacığında çalışacağını unutmayın. İçin tüm diğer iş parçacıkları veya bağlamları aynı uygulama etki alanında, alanları başlatılacak `null` (`Nothing` Visual Basic'te) başvuru türleridir veya varsayılan değer türleri olmaları durumunda değerleri. Bu nedenle, iş parçacığı göreli statik alanları başlatmak için sınıf oluşturucuları güvenmemelisiniz. Bunun yerine, iş parçacığı göreli statik alanları başlatma önlemek ve bunlar için başlatılır varsayar `null` (`Nothing`) veya varsayılan değerlerine.  
  
## <a name="data-slots"></a>Veri yuvaları  
 .NET Framework, bir iş parçacığı ve uygulama etki alanı birleşimi için benzersiz olan dinamik veri yuvaları sağlar. İki tür veri yuvaları: yuvaları ve adlandırılmamış yuvaları adlı. Her ikisi de kullanılarak uygulanır <xref:System.LocalDataStoreSlot> yapısı.  
  
-   Bir adlandırılmış veri yuvası oluşturmak için kullanın <xref:System.Threading.Thread.AllocateNamedDataSlot%2A?displayProperty=nameWithType> veya <xref:System.Threading.Thread.GetNamedDataSlot%2A?displayProperty=nameWithType> yöntemi. Mevcut bir yuva adlı bir başvuru almak için adının geçirmek <xref:System.Threading.Thread.GetNamedDataSlot%2A> yöntemi.  
  
-   Adlandırılmamış yuvası oluşturmak için kullanın <xref:System.Threading.Thread.AllocateDataSlot%2A?displayProperty=nameWithType> yöntemi.  
  
 Hem adlandırılmış hem de adlandırılmamış yuvaları, kullanın <xref:System.Threading.Thread.SetData%2A?displayProperty=nameWithType> ve <xref:System.Threading.Thread.GetData%2A?displayProperty=nameWithType> yuvasındaki bilgilerini almak ve ayarlamak için yöntemleri. Bunlar her zaman bunları şu anda yürütülmekte olan iş parçacığı için veriler üzerinde işlem statik yöntemlerdir.  
  
 Adını geçirerek gerektiğinde yuvası almak için adlandırılmış yuvaları uygun, olabilir <xref:System.Threading.Thread.GetNamedDataSlot%2A> yerine bir başvuru adlandırılmamış bir yuvaya yöntemi. Ancak, başka bir bileşen kendi iş parçacığı göreli depolama için aynı adı kullanıyorsa ve bir iş parçacığı hem kodunuz hem de başka bir bileşen kodu yürütür, iki bileşeni birbirlerinin veri bozulmasına neden olabilir. (Bu senaryoda, her iki bileşenin aynı uygulama etki alanında çalıştığından ve bunlar aynı verilere paylaşmayı tasarlanmamıştır varsayılmaktadır.)  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ContextStaticAttribute>
- <xref:System.Threading.Thread.GetNamedDataSlot%2A?displayProperty=nameWithType>
- <xref:System.ThreadStaticAttribute>
- <xref:System.Runtime.Remoting.Messaging.CallContext>
- [İş parçacığı oluşturma](../../../docs/standard/threading/index.md)
