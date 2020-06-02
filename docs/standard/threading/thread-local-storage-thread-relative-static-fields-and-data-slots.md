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
ms.openlocfilehash: adeeb6c95769d8e1ac120d4fb26d8aaedf7a1d4d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291090"
---
# <a name="thread-local-storage-thread-relative-static-fields-and-data-slots"></a>İş Parçacığında Yerel Depolama: İş Parçacığı Göreli Statik Alanları ve Veri Yuvaları
İş parçacığı ve uygulama etki alanına özgü verileri depolamak için yönetilen iş parçacığı yerel depolaması (TLS) kullanabilirsiniz. .NET Framework yönetilen TLS kullanmak için iki yol sunar: iş parçacığı göreli statik alanları ve veri yuvaları.  
  
- Derleme zamanında tam ihtiyaçlarınızı önleyebiliyorsanız, iş parçacığı göreli statik alanları (Visual Basic iş parçacığı göreli `Shared` alanları) kullanın. İş parçacığı göreli statik alanları en iyi performansı sağlar. Ayrıca, derleme zamanı tür denetimi 'nin avantajlarını da sunar.  
  
- Gerçek gereksinimleriniz yalnızca çalışma zamanında keşfedildiğinde veri yuvalarını kullanın. Veri yuvaları, iş parçacığı göreli statik alanlarından daha yavaş ve daha fazla kullanım açısından daha yavaştır ve veriler tür olarak depolanır, bu <xref:System.Object> nedenle kullanmadan önce doğru türe atamalısınız.  
  
 Yönetilmeyen C++ ' da, `TlsAlloc` yuvaları dinamik olarak ayırmak ve `__declspec(thread)` bir değişkenin iş parçacığı göreli depolamada ayrılması gerektiğini bildirmek için kullanırsınız. İş parçacığı göreli statik alanları ve veri yuvaları, bu davranışın yönetilen sürümünü sağlar.  
  
 .NET Framework 4 ' te, <xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType> nesne ilk tüketildiği zaman geç başlatılan iş parçacığı yerel nesneleri oluşturmak için sınıfını kullanabilirsiniz. Daha fazla bilgi için bkz. [yavaş başlatma](../../framework/performance/lazy-initialization.md).  
  
## <a name="uniqueness-of-data-in-managed-tls"></a>Yönetilen TLS 'deki verilerin benzersizliği  
 İş parçacığı göreli statik alanları veya veri yuvaları kullanmanıza bakılmaksızın, yönetilen TLS 'deki veriler, iş parçacığı ve uygulama etki alanı birleşimine özgüdür.  
  
- Bir uygulama etki alanı içinde, her iki iş parçacığı aynı alanı veya yuvayı kullandıklarında bile, bir iş parçacığı başka bir iş parçacığından verileri değiştiremez.  
  
- Bir iş parçacığı birden çok uygulama etki alanından aynı alana veya yuvaya eriştiğinde, her uygulama etki alanında ayrı bir değer tutulur.  
  
 Örneğin, bir iş parçacığı iş parçacığı göreli statik alanının değerini ayarlarsa, başka bir uygulama etki alanı girer ve sonra alanın değerini alıyorsa ikinci uygulama etki alanında alınan değer ilk uygulama etki alanındaki değerden farklıdır. İkinci uygulama etki alanındaki alan için yeni bir değer ayarlandığında, ilk uygulama etki alanındaki alanın değeri etkilenmez.  
  
 Benzer şekilde, bir iş parçacığı iki farklı uygulama etki alanında aynı adlandırılmış veri yuvasını aldığında, ilk uygulama etki alanındaki veriler ikinci uygulama etki alanındaki verilerden bağımsız kalır.  
  
## <a name="thread-relative-static-fields"></a>İş parçacığı göreli statik alanları  
 Bir veri parçasının her zaman bir iş parçacığı ve uygulama-etki alanı birleşimine benzersiz olduğunu biliyorsanız, <xref:System.ThreadStaticAttribute> özniteliğini statik alana uygulayın. Diğer herhangi bir statik alanı kullandığınız için alanı kullanın. Alanındaki veriler, onu kullanan her iş parçacığı için benzersizdir.  
  
 İş parçacığı göreli statik alanları, veri yuvalardan daha iyi performans sağlar ve derleme zamanı tür denetimi avantajına sahiptir.  
  
 Tüm sınıf Oluşturucu kodunun alana erişen ilk bağlamdaki ilk iş parçacığında çalışacağını unutmayın. Aynı uygulama etki alanındaki diğer tüm iş parçacıklarında veya bağlamlarda, alanlar `null` `Nothing` başvuru türlerseler (Visual Basic olarak) veya değer türlerseler varsayılan değerleriyle başlatılır. Bu nedenle, iş parçacığı göreli statik alanlarını başlatmak için sınıf oluşturucularına güvenmemelisiniz. Bunun yerine, iş parçacığı göreli statik alanları başlatmaktan kaçının ve bunların `null` ( `Nothing` ) ya da varsayılan değerlerine başlatıldığını varsayın.  
  
## <a name="data-slots"></a>Veri yuvaları  
 .NET Framework, iş parçacığı ve uygulama-etki alanı birleşimine özgü dinamik veri yuvaları sağlar. İki tür veri yuvası vardır: adlandırılmış yuvalar ve adlandırılmamış yuvalar. Her ikisi de yapı kullanılarak uygulanır <xref:System.LocalDataStoreSlot> .  
  
- Adlandırılmış bir veri yuvası oluşturmak için <xref:System.Threading.Thread.AllocateNamedDataSlot%2A?displayProperty=nameWithType> veya <xref:System.Threading.Thread.GetNamedDataSlot%2A?displayProperty=nameWithType> yöntemini kullanın. Var olan bir adlandırılmış yuvaya başvuru almak için, adını <xref:System.Threading.Thread.GetNamedDataSlot%2A> yöntemine geçirin.  
  
- Adlandırılmamış bir veri yuvası oluşturmak için <xref:System.Threading.Thread.AllocateDataSlot%2A?displayProperty=nameWithType> yöntemini kullanın.  
  
 Hem adlandırılmış hem de adlandırılmamış yuvalarda, <xref:System.Threading.Thread.SetData%2A?displayProperty=nameWithType> <xref:System.Threading.Thread.GetData%2A?displayProperty=nameWithType> yuvadaki bilgileri ayarlamak ve almak için ve yöntemlerini kullanın. Bunlar, şu anda yürütülmekte olan iş parçacığı için verileri her zaman işleyen statik yöntemlerdir.  
  
 Adlandırılmış yuvalar kullanışlı olabilir, çünkü <xref:System.Threading.Thread.GetNamedDataSlot%2A> Adsız bir yuvaya bir başvuru tutmak yerine, adını yöntemine geçirerek bu yuvayı elde edebilirsiniz. Ancak, başka bir bileşen iş parçacığı göreli depolaması için aynı adı kullanıyorsa ve bir iş parçacığı hem bileşeninizden hem de diğer bileşenden kod çalıştırırsa, iki bileşen birbirlerinin verilerinin bozulmasına neden olabilirler. (Bu senaryo her iki bileşenin aynı uygulama etki alanında çalıştığını ve aynı verilerin paylaşılması için tasarlanmadığı varsayılır.)  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ContextStaticAttribute>
- <xref:System.Threading.Thread.GetNamedDataSlot%2A?displayProperty=nameWithType>
- <xref:System.ThreadStaticAttribute>
- <xref:System.Runtime.Remoting.Messaging.CallContext>
- [İş Parçacığı Oluşturma](index.md)
