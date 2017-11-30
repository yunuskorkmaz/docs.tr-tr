---
title: "Yan Yana Yürütme için Bileşen Oluşturma Yönergeleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- side-by-side execution, multiple application versions
- side-by-side execution, multiple component versions
ms.assetid: 5c540161-6e40-42e9-be92-6175aee2c46a
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 054744612ec54861f675005a27a309e00024b242
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="guidelines-for-creating-components-for-side-by-side-execution"></a>Yan Yana Yürütme için Bileşen Oluşturma Yönergeleri
Yönetilen uygulamalar veya yan yana yürütme için tasarlanmış bileşenleri oluşturmak için aşağıdaki genel yönergeleri izleyin:  
  
-   Tür kimliği dosya belirli bir sürümü bağlayın.  
  
     Ortak dil çalışma zamanı tür kimliğini tanımlayıcı adlı derlemeler kullanarak belirli dosya sürümüne bağlar. Bir uygulama veya yan yana yürütme için bileşen oluşturmak için tüm derlemelerin tanımlayıcı bir ad vermeniz gerekir. Bu, kesin türü kimliği oluşturur ve doğru dosya türü çözümlemesi yönlendirilir sağlar. Tanımlayıcı adlı bir derleme, sürüm, kültür ve çalışma zamanı bağlama isteği gerçekleştirmek için doğru dosyayı bulmak için kullandığı yayımcı bilgilerini içerir.  
  
-   Sürüm algılayan depolama kullanın.  
  
     Çalışma zamanı sürümü kullanan depolama sağlamak için genel derleme önbelleği kullanır. Genel Derleme Önbelleği, .NET Framework kullanan her bilgisayarda yüklü bir sürümünü kullanan dizin yapısıdır. Bu derleme yeni bir sürümü yüklü olduğunda genel derleme önbelleğinde yüklü derlemelerin üzerine yazılmaz.  
  
-   Bir uygulama veya yalıtımlı şekilde çalışır bileşeni oluşturun.  
  
     Bir uygulama veya yalıtımlı şekilde çalışır bileşeni uygulama veya bileşenin iki örneği aynı anda çalıştırırken çakışmaları önlemek için kaynak yönetmeniz gerekir. Ayrıca uygulama veya bileşenin sürüme özgü dosya yapısı kullanmanız gerekir.  
  
## <a name="application-and-component-isolation"></a>Uygulama ve bileşen yalıtımı  
 Bir uygulama veya bileşen yan yana yürütme için başarıyla tasarlamak için bir yalıtım anahtardır. Uygulamanın veya bileşenin gerekir tüm kaynakları yönetebilir, özellikle g/ç, yalıtılmış bir şekilde dosya. Uygulama veya bileşenin yalıtım modunda çalışacağından emin olmak için aşağıdaki yönergeleri izleyin:  
  
-   Kayıt defterine bir sürüme özgü biçimde yazın. Değerleri kovanları veya sürüm belirtmek ve bilgi ya da durum bileşen sürümleri arasında paylaştırma anahtarları depolayın. Bu iki uygulamanın ya da bilgi üzerine yazılmasını aynı anda çalışan bileşenleri önler.  
  
-   Böylece bir yarış durumu oluşmaz adlandırılmış çekirdek nesneleri sürüme özgü yapın. Bir yarış durumu gibi aynı uygulamanın iki sürümlerinden iki semafor diğer bağlı bekleme oluşur.  
  
-   Dosya ve dizin adları sürüm farkında olun. Bu dosya yapıları sürümü bilgilerini yararlanmalıdır anlamına gelir.  
  
-   Kullanıcı hesapları ve grupları bir sürüme özgü şekilde oluşturun. Kullanıcı hesapları ve grupları bir uygulama tarafından oluşturulan sürümü tarafından tanıtılmalıdır. Kullanıcı hesapları ve grupları uygulama sürümleri arasında paylaşmayın.  
  
## <a name="installing-and-uninstalling-versions"></a>Yükleme ve sürümleri kaldırma  
 Yan yana yürütme için bir uygulama tasarlarken, yükleme ve sürümleri kaldırma ile ilgili aşağıdaki yönergeleri izleyin:  
  
-   Bilgi farklı bir .NET Framework sürümü altında çalışan diğer uygulamalar tarafından gerekli olabilecek kayıt defterinden silmeyin.  
  
-   Farklı bir .NET Framework sürümü altında çalışan diğer uygulamalar tarafından gerekli olabilecek kayıt defterindeki bilgiler değiştirmeyin.  
  
-   Farklı bir .NET Framework sürümü altında çalışan diğer uygulamalar tarafından gerekli olabilecek COM bileşenlerini kaydı yok.  
  
-   Değiştirmeyin **Inprocserver32** veya diğer kayıt defteri girdileri zaten kayıtlı bir COM sunucusu.  
  
-   Kullanıcı hesapları veya farklı bir .NET Framework sürümü altında çalışan diğer uygulamalar tarafından gerekli olabilecek silmeyin.  
  
-   Herhangi bir sürüm bilgisi olmayan yolu içeren kayıt defterine eklemeyin.  
  
## <a name="file-version-number-and-assembly-version-number"></a>Dosya sürüm numarası ve derleme sürüm numarası  
 Dosya, çalışma zamanı tarafından kullanılmayan bir Win32 sürümü kaynak sürümüdür. Genel olarak, bir yerinde güncelleştirme için bile dosya sürümünü güncelleştirin. İki özdeş dosyaların farklı dosya sürümü bilgilerini olabilir ve iki farklı dosyaları aynı dosya sürümü bilgilerini olabilir.  
  
 Derleme sürümü için derleme bağlama çalışma zamanı tarafından kullanılır. İki özdeş derlemeleri farklı sürüm numaralarını ile iki farklı derlemeleri olarak çalışma zamanı tarafından kabul edilir.  
  
 [Genel Derleme Önbelleği Aracı (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) yalnızca dosyanın sürüm numarası daha yeni olduğunda bütünleştirilmiş değiştirmenizi sağlar. Derleme sürüm numarasını büyük olmadıkça yükleyici bütünleştirilmiş genellikle yüklemez.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yan yana yürütme](../../../docs/framework/deployment/side-by-side-execution.md)  
 [Nasıl yapılır: etkinleştirme ve otomatik bağlama yönlendirmesini devre dışı](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)
