---
title: "İş Parçacığı Yerel Deposu: İş Parçacığı Göreli Statik Alanları ve Veri Yuvaları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], local storage
- threading [.NET Framework], thread-relative static fields
- local thread storage
- TLS
ms.assetid: c633a4dc-a790-4ed1-96b5-f72bd968b284
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 127f7ea9bb6a6bf91547d049f582439882d2fb6e
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="thread-local-storage-thread-relative-static-fields-and-data-slots"></a>İş Parçacığı Yerel Deposu: İş Parçacığı Göreli Statik Alanları ve Veri Yuvaları
İş parçacığı ve uygulama etki alanı için benzersiz olan yönetilen iş parçacığı yerel depolaması (TLS) verileri depolamak için kullanabilirsiniz. .NET Framework kullanmanın iki yolu yönetilen TLS sağlar: iş parçacığı göreli statik alanları ve veri yuvaları.  
  
-   İş parçacığı göreli statik alanları kullanın (iş parçacığı göreli `Shared` alanları Visual Basic'te) tam ihtiyaçlarınıza derleme zamanında öngörüyorsanız. İş parçacığı göreli statik alanları en iyi performans sağlar. Bunlar ayrıca, derleme zamanı tür denetimi avantajlarını sağlar.  
  
-   Gerçek gereksinimler yalnızca çalışma zamanında bulunan veri yuvaları kullanın. Veri yuvaları daha yavaş ve daha iş parçacığı göreli statik alanları kullanmak garip ve veri türü olarak depolanan <xref:System.Object>, bu nedenle, kullanmadan önce doğru türüne dönüştürmeniz gerekir.  
  
 Yönetilmeyen C++'da, kullandığınız `TlsAlloc` yuvaları dinamik olarak ayırabilir ve `__declspec(thread)` bir değişken iş parçacığı göreli depoda ayrılmalıdır bildirmek için. İş parçacığı göreli statik alanları ve veri yuvaları Bu davranış yönetilen bir sürümünü sağlayın.  
  
 İçinde [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], kullanabileceğiniz <xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType> nesne ilk kullanıldığında gevşek başlatılmış iş parçacığı yerel nesneleri oluşturmak için sınıf. Daha fazla bilgi için bkz: [geç başlatma](../../../docs/framework/performance/lazy-initialization.md).  
  
## <a name="uniqueness-of-data-in-managed-tls"></a>Yönetilen TLS veri benzersizliği  
 İş parçacığı göreli statik alanları veya veri yuvaları kullanıp yönetilen TLS veriler iş parçacığı ve uygulama etki alanı birleşimi benzersiz bağlıdır.  
  
-   Her iki iş parçacığı aynı alan veya yuva kullandığınızda da bir uygulama etki alanı içinde başka bir iş parçacığı, verileri bir iş parçacığı değiştiremezsiniz.  
  
-   Bir iş parçacığı birden çok uygulama etki alanından aynı alan veya yuvası eriştiğinde, ayrı bir değeri her uygulama etki alanında korunur.  
  
 Örneğin, bir iş parçacığı ayarlarsa iş parçacığı göreli statik alanının değeri başka bir uygulama etki alanı girer ve alanın değerini alır, ikinci uygulama etki alanında alınan değeri ilk uygulama etki alanı değeri farklılık gösterir. İkinci uygulama etki alanı için yeni bir değer ayarı ilk uygulama etki alanın değerini etkilemez.  
  
 Benzer şekilde, bir iş parçacığı iki farklı uygulama etki alanları aynı adlandırılmış veri yuvasında aldığında, ilk uygulama etki alanı veriler ikinci uygulama etki alanındaki verilerden bağımsız olarak kalır.  
  
## <a name="thread-relative-static-fields"></a>İş parçacığı göreli statik alanları  
 Veri parçası her zaman bir iş parçacığı ve uygulama etki alanı birleşimi benzersiz olduğunu biliyorsanız, uygulama <xref:System.ThreadStaticAttribute> özniteliği statik alan. Herhangi bir statik alan kullanacağınız alan kullanın. Alan verileri kullanan her bir iş parçacığı için benzersizdir.  
  
 İş parçacığı göreli statik alanları veri yuvaları daha iyi performans sağlar ve derleme zamanı tür denetimi avantajına sahiptir.  
  
 Herhangi bir sınıf oluşturucu kodu alan erişen ilk bağlamında ilk iş parçacığı üzerinde çalışacağını unutmayın. İçin tüm diğer iş parçacıkları veya aynı uygulama etki alanı bağlamlarda, alanları başlatılacak `null` (`Nothing` Visual Basic'te) başvuru türleri oldukları veya türleri olmaları durumunda değerleri için varsayılan değer. Bu nedenle, iş parçacığı göreli statik alanları başlatmak için sınıf oluşturucular güvenmemelisiniz. Bunun yerine, iş parçacığı göreli statik alanları başlatma önlemek ve bunlar için başlatılır varsayın `null` (`Nothing`) veya varsayılan değerlerine.  
  
## <a name="data-slots"></a>Veri yuvaları  
 .NET Framework birleşimi iş parçacığı ve uygulama etki alanı için benzersiz dinamik veri yuvaları sağlar. İki tür veri yuvaları: yuvaları ve adsız yuvaları adlı. Her ikisi de kullanılarak uygulanan <xref:System.LocalDataStoreSlot> yapısı.  
  
-   Bir adlandırılmış veri yuva oluşturmak üzere kullanmanız <xref:System.Threading.Thread.AllocateNamedDataSlot%2A?displayProperty=nameWithType> veya <xref:System.Threading.Thread.GetNamedDataSlot%2A?displayProperty=nameWithType> yöntemi. Varolan bir yuva adlı bir başvuru almak için adının geçirmek <xref:System.Threading.Thread.GetNamedDataSlot%2A> yöntemi.  
  
-   Adlandırılmamış yuvası oluşturmak üzere kullanmanız <xref:System.Threading.Thread.AllocateDataSlot%2A?displayProperty=nameWithType> yöntemi.  
  
 Hem adlandırılmış ve adlandırılmamış yuvaları için kullanmak <xref:System.Threading.Thread.SetData%2A?displayProperty=nameWithType> ve <xref:System.Threading.Thread.GetData%2A?displayProperty=nameWithType> ayarlamak ve yuva bilgileri almak için yöntemleri. Bunları şu anda yürütülmekte iş parçacığı için veriler her zaman hareket statik yöntemler şunlardır.  
  
 Adının geçirerek ihtiyacınız olduğunda, yuva alabilirsiniz çünkü adlandırılmış yuvaları uygun, olabilir <xref:System.Threading.Thread.GetNamedDataSlot%2A> adlandırılmamış yuvası başvuru koruma yerine yöntemi. Ancak, başka bir bileşenin iş parçacığı göreli depolama alanı için aynı adı kullanan ve bir iş parçacığı bileşeniniz hem diğer bileşeni kodu yürütür, iki bileşenden diğer kişilerin veri bozulmasına neden olabilir. (Bu senaryoda, her iki bileşenin aynı uygulama etki alanında çalıştığından ve bunlar aynı veri paylaşmak için tasarlanmamıştır varsayar.)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ContextStaticAttribute>  
 <xref:System.Threading.Thread.GetNamedDataSlot%2A?displayProperty=nameWithType>  
 <xref:System.ThreadStaticAttribute>  
 <xref:System.Runtime.Remoting.Messaging.CallContext>  
 [İş parçacığı oluşturma](../../../docs/standard/threading/index.md)
