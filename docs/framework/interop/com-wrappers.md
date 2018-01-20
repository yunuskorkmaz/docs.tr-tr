---
title: "COM Sarmalayıcıları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- wrapper classes
- COM interop, COM wrappers
- COM wrappers
- COM, wrappers
- interoperation with unmanaged code, COM wrappers
- COM callable wrappers
ms.assetid: e56c485b-6b67-4345-8e66-fd21835a6092
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b899ed162fa626f8c378923907f275cebf9a7db4
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="com-wrappers"></a>COM Sarmalayıcıları
COM birçok önemli yoldan .NET Framework nesne modelinden farklıdır:  
  
-   COM nesneleri istemcileri bu nesnelerin ömrü yönetmeniz gerekir; Ortak dil çalışma zamanı kendi ortamında nesnelerin ömrü yönetir.  
  
-   COM nesneleri istemcileri, hizmet bu hizmeti sağlayan bir arabirimi isteme ve bir arabirim işaretçisi veya geri alma kullanılabilir olup olmadığını bulur. .NET nesneleri istemcileri yansıma kullanarak bir nesnenin işlevlerinin açıklaması elde edebilirsiniz.  
  
-   .NET Framework yürütme ortamı tarafından yönetilen bellekte NET nesneleri bulunur. Yürütme Ortamı, performans nedenleriyle bellekte nesneleri hareket ettirin ve hareket nesneleri yapılan tüm başvuruları güncelleştirin. Yönetilmeyen istemciler, bir nesne için bir işaretçi elde aynı konumda kalır nesnesine bağlıdır. Bu istemciler, konumu sabitlenmemiş bir nesneyle ilgili hiçbir mekanizması vardır.  
  
 Bu farklılıklar aşmak için çalışma zamanı ilgili ortamlarına nesnelerinde aradığınız düşündüğünüz yönetilen ve yönetilmeyen istemcileri yapmak için sarmalayıcı sınıflar sağlar. Yönetilen istemci bir COM nesnesi üzerinde bir yöntemi çağırır her çalışma zamanı oluşturur bir [çalışma zamanı aranabilir sarmalayıcısı](../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW). RCWs başka şeylerin yönetilen ve yönetilmeyen başvuru mekanizmaları arasındaki farklar soyut. Çalışma zamanı da oluşturur bir [COM aranabilir sarmalayıcısı](../../../docs/framework/interop/com-callable-wrapper.md) sorunsuz bir .NET nesnesinde bir yöntemi çağırmak bir COM istemci etkinleştirme işlemi geri almak için (saat). Aşağıdaki çizimde gösterildiği gibi çağrıyı yapan kod açısından çalışma zamanı oluşturur hangi sarmalayıcı sınıfı belirler.  
  
 ![COM sarmalayıcı genel bakış](../../../docs/framework/interop/media/bidirectional.gif "çift yönlü")  
COM sarmalayıcı genel bakış  
  
 Çoğu durumda, COM ve .NET Framework arasında sınır arası çağrılar için yeterli hazırlama standart RCW veya çalışma zamanı tarafından oluşturulan saatin tersi YÖNDE sağlar. Özel öznitelikler kullanarak, çalışma zamanı temsil eden yönetilen ve yönetilmeyen kod yolu isteğe bağlı olarak ayarlayabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Gelişmiş COM birlikte çalışabilirliği](http://msdn.microsoft.com/library/3ada36e5-2390-4d70-b490-6ad8de92f2fb)  
 [Çalışma Zamanında Çağrılabilir Sarmalayıcı](../../../docs/framework/interop/runtime-callable-wrapper.md)  
 [COM Çağrılabilir Sarmalayıcısı](../../../docs/framework/interop/com-callable-wrapper.md)  
 [Standart sarmalayıcıları özelleştirme](http://msdn.microsoft.com/library/c40d089b-6a3c-41b5-a20d-d760c215e49d)  
 [Nasıl yapılır: çalışma zamanı aranabilir sarmalayıcıları özelleştirme](http://msdn.microsoft.com/library/4a4bb3da-4d60-4517-99f2-78d46a681732)
