---
title: Yan Yana Yürütme için Bileşen Oluşturma Yönergeleri
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution, multiple application versions
- side-by-side execution, multiple component versions
ms.assetid: 5c540161-6e40-42e9-be92-6175aee2c46a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0e88ba4260e9deaf53ae828f222d32f8ece61ffa
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59151040"
---
# <a name="guidelines-for-creating-components-for-side-by-side-execution"></a>Yan Yana Yürütme için Bileşen Oluşturma Yönergeleri
Yan yana yürütme için tasarlanmış bileşen ya da yönetilen uygulamalar oluşturmak için aşağıdaki genel yönergeleri izleyin:  
  
-   Türü kimlik, bir dosyanın belirli bir sürüme bağlayın.  
  
     Ortak dil çalışma zamanı, tanımlayıcı adlı derlemeler kullanarak, belirli dosya sürümüne türü kimlik bağlar. Bir uygulama veya yan yana yürütme için bileşen oluşturmak için tüm derlemelerin tanımlayıcı bir ad vermeniz gerekir. Bu, kesin türü kimliği oluşturur ve herhangi bir tür çözümlemesi için doğru dosya yönlendirilir sağlar. Bir katı adlı derleme sürüm, kültür ve çalışma zamanı, bağlama isteği yerine getirmek için doğru dosyayı bulmak için kullanır. yayımcı bilgilerini içerir.  
  
-   Sürüm algılayan depolamayı kullanın.  
  
     Çalışma zamanı, genel derleme önbelleğinde sürüm ile uyumlu depolama sağlamak için kullanır. Genel Derleme Önbelleği, .NET Framework kullanan her bir bilgisayarda yüklü bir sürümü kullanan dizin yapısıdır. Bu derleme için yeni bir sürümü yüklü olduğunda derlemeleri genel derleme önbelleğinde yüklü üzerine yazılmaz.  
  
-   Bir uygulama veya yalıtım modunda çalışan bir bileşen oluşturun.  
  
     Bir uygulama veya yalıtım modunda çalışan bir bileşen, uygulamanın veya bileşenin iki örneği aynı anda çalıştırılırken, çakışmaları önlemek için kaynakları yönetmeniz gerekir. Ayrıca uygulama veya bileşenin bir sürüme özgü dosya yapısı kullanmanız gerekir.  
  
## <a name="application-and-component-isolation"></a>Uygulama ve bileşen yalıtım  
 Başarılı bir uygulama veya yan yana yürütme için bileşen tasarlamak için bir anahtar yalıtımı ' dir. Uygulama veya bileşen gereken tüm kaynakları yönetebilir, özellikle g/ç, yalıtılmış bir şekilde dosya. Uygulama veya bileşen yalıtım modunda çalıştığından emin olmak için aşağıdaki yönergeleri izleyin:  
  
-   Kayıt defterine bir sürüme özgü şekilde yazın. Yığınlar veya sürümü belirtmek ve bilgi veya durumu bileşen sürümleri arasında paylaşmayın anahtarları değerleri Store. Bu iki uygulamanın ya da bilgi yazmasını aynı anda çalışan bileşenleri engeller.  
  
-   Adlandırılmış çekirdek nesneleri sürüme özgü kılmak bir yarış durumu oluşmaz. Örneğin, aynı uygulamayı iki sürümlerinden iki semaforları birbirine beklerken bir yarış durumu oluşur.  
  
-   Dosya ve dizin adları sürüm farkında olun. Bu dosya yapıları sürüm bilgisi esas yararlanmalıdır anlamına gelir.  
  
-   Kullanıcı hesapları ve grupları bir sürüme özgü bir şekilde oluşturun. Kullanıcı hesapları ve grupları bir uygulama tarafından oluşturulan sürüm tarafından tanıtılmalıdır. Kullanıcı hesaplarını ve grupları bir uygulamanın sürümleri arasında paylaşmayın.  
  
## <a name="installing-and-uninstalling-versions"></a>Yükleme ve sürümleri kaldırma  
 Yan yana yürütme için bir uygulama tasarlarken, yükleme ve sürümleri kaldırma ile ilgili aşağıdaki yönergeleri izleyin:  
  
-   .NET Framework'ün altında farklı bir sürümünü çalıştıran diğer uygulamalar tarafından gerekli olabilecek kayıt defterinden bilgi silmeyin.  
  
-   .NET Framework'ün altında farklı bir sürümünü çalıştıran diğer uygulamalar tarafından gerekli olabilecek kayıt defteri bilgilerini değiştirmeyin.  
  
-   .NET Framework'ün altında farklı bir sürümünü çalıştıran diğer uygulamalar tarafından gerekli olabilecek COM bileşenlerini kaydı değildir.  
  
-   Değişmez **Inprocserver32** veya diğer önceden kaydedilmiş bir COM sunucusu için kayıt defteri girdileri.  
  
-   Kullanıcı hesapları veya farklı bir .NET Framework sürümünde çalışan diğer uygulamalar tarafından gerekli olabilecek grupları silmeyin.  
  
-   Herhangi bir sürüm bilgisi olmayan yolunu içeren bir kayıt defterine eklemeyin.  
  
## <a name="file-version-number-and-assembly-version-number"></a>Dosyanın sürüm numarası ve derleme sürüm numarası  
 Dosya, çalışma zamanı tarafından kullanılmayan bir Win32 sürüm kaynağı sürümüdür. Genel olarak, bir yerinde güncelleştirme için bile dosya sürümünü güncelleştirin. İki özdeş dosyaların farklı dosya sürümü bilgilerini olabilir ve iki farklı dosyalar aynı dosya sürümü bilgilerini olabilir.  
  
 Derleme sürümü, derleme bağlama için çalışma zamanı tarafından kullanılır. İki özdeş derlemenin farklı sürüm numaralarıyla çalışma zamanı tarafından iki farklı derlemeler kabul edilir.  
  
 [Genel Derleme Önbelleği aracını (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) yalnızca dosyanın sürüm numarası yeni olduğunda bir derlemeyi çoğaltmanıza imkan tanır. Derleme sürüm numarasının büyük olmadığı sürece yükleyici bütünleştirilmiş genel olarak yüklemez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yan Yana Yürütme](../../../docs/framework/deployment/side-by-side-execution.md)
- [Nasıl yapılır: Otomatik bağlama yeniden yönlendirmesini devre dışı bırakma ve etkinleştirme](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)
