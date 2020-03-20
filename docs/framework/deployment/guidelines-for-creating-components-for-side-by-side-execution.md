---
title: Yan Yana Yürütme için Bileşen Oluşturma Yönergeleri
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution, multiple application versions
- side-by-side execution, multiple component versions
ms.assetid: 5c540161-6e40-42e9-be92-6175aee2c46a
ms.openlocfilehash: 42d0e2d85517d4a8fb443db9b63e6b893267caca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73121582"
---
# <a name="guidelines-for-creating-components-for-side-by-side-execution"></a>Yan Yana Yürütme için Bileşen Oluşturma Yönergeleri
Yan yana yürütme için tasarlanmış yönetilen uygulamalar veya bileşenler oluşturmak için aşağıdaki genel yönergeleri izleyin:  
  
- Türü kimliği bir dosyanın belirli bir sürümüne bağla.  
  
     Ortak dil çalışma süresi, güçlü adlandırılmış derlemeler kullanarak kimlik türünü belirli bir dosya sürümüne bağlar. Yan yana yürütme için bir uygulama veya bileşen oluşturmak için, tüm derlemelere güçlü bir ad vermeniz gerekir. Bu, kesin tür kimliği oluşturur ve herhangi bir tür çözünürlüğünün doğru dosyaya yönlendirilmesini sağlar. Güçlü adlandırılmış derleme, bağlama isteğini yerine getirmek için doğru dosyayı bulmak için çalışma zamanının kullandığı sürüm, kültür ve yayımcı bilgilerini içerir.  
  
- Sürüm farkında depolama alanını kullanın.  
  
     Çalışma süresi, sürüm eğitim alanını sağlamak için genel montaj önbelleğini kullanır. Genel derleme önbelleği, .NET Framework kullanan her bilgisayara yüklenen sürüm farkında bir dizin yapısıdır. Bu derlemenin yeni bir sürümü yüklendiğinde, genel derleme önbelleğine yüklenen derlemeler üzerine yazılmaz.  
  
- Yalıtımlı çalışan bir uygulama veya bileşen oluşturun.  
  
     Yalıtımlı çalışan bir uygulama veya bileşen, uygulamanın veya bileşenin iki örneği aynı anda çalıştığında çakışmaları önlemek için kaynakları yönetmelidir. Uygulama veya bileşen de bir sürüm özel dosya yapısı kullanmanız gerekir.  
  
## <a name="application-and-component-isolation"></a>Uygulama ve Bileşen İzolasyon  
 Yan yana yürütme için bir uygulamayı veya bileşeni başarıyla tasarlamanın bir anahtarı yalıtımdır. Uygulama veya bileşen, özellikle dosya G/Ç olmak üzere tüm kaynakları yalıtılmış bir şekilde yönetmelidir. Uygulamanızın veya bileşeninizin izole çalıştığından emin olmak için aşağıdaki yönergeleri izleyin:  
  
- Kayıt defterine sürüme özgü bir şekilde yazın. Değerleri sürümü gösteren kovanlarda veya anahtarlarda depolayın ve bilgileri paylaşmayın veya bileşenin sürümleri arasında durum belirtin. Bu, iki uygulamanın veya bileşenin aynı anda çalışmasını önler.  
  
- Bir yarış koşulu oluşmaması için adlandırılmış çekirdek nesneleri sürümüne özgü olun. Örneğin, aynı uygulamanın iki sürümünden iki semafor birbiri üzerine beklemede bir yarış koşulu oluşur.  
  
- Dosya ve dizin adlarını sürüm farkında hale getirin. Bu, dosya yapılarının sürüm bilgilerine dayanması gerektiği anlamına gelir.  
  
- Kullanıcı hesaplarını ve grupları sürüme özgü bir şekilde oluşturun. Bir uygulama tarafından oluşturulan kullanıcı hesapları ve grupları sürümle tanımlanmalıdır. Kullanıcı hesaplarını ve gruplarını bir uygulamanın sürümleri arasında paylaşmayın.  
  
## <a name="installing-and-uninstalling-versions"></a>Sürümleri Yükleme ve Kaldırma  
 Yan yana yürütme için bir uygulama tasarlarken, sürümleri yükleme ve kaldırma yla ilgili aşağıdaki yönergeleri izleyin:  
  
- .NET Framework'ün farklı bir sürümü altında çalışan diğer uygulamaların ihtiyaç duyulabileceği bilgileri kayıt defterinden silmeyin.  
  
- .NET Framework'ün farklı bir sürümü altında çalışan diğer uygulamaların ihtiyaç duyulabileceği bilgileri kayıt defterinde değiştirmeyin.  
  
- .NET Framework'ün farklı bir sürümü altında çalışan diğer uygulamaların ihtiyaç duyulabileceği COM bileşenlerinin kaydını silmeyin.  
  
- **InprocServer32** veya daha önce kaydedilmiş bir COM sunucusu için diğer kayıt defteri girişlerini değiştirmeyin.  
  
- .NET Framework'ün farklı bir sürümü altında çalışan diğer uygulamaların ihtiyaç duyulabileceği kullanıcı hesaplarını veya gruplarını silmeyin.  
  
- Kayıt defterine, kullanılmayan bir yol içeren hiçbir şey eklemeyin.  
  
## <a name="file-version-number-and-assembly-version-number"></a>Dosya Sürüm Numarası ve Montaj Sürüm Numarası  
 Dosya sürümü, çalışma zamanı tarafından kullanılmayan bir Win32 sürüm kaynağıdır. Genel olarak, yerinde bir güncelleştirme için bile dosya sürümünü güncellersiniz. İki özdeş dosya farklı dosya sürümü bilgilerine sahip olabilir ve iki farklı dosya aynı dosya sürümü bilgilerine sahip olabilir.  
  
 Derleme sürümü, derleme bağlama için çalışma zamanı tarafından kullanılır. Farklı sürüm numaralarına sahip iki özdeş derleme, çalışma süresine göre iki farklı derleme olarak kabul edilir.  
  
 [Genel Derleme Önbellek aracı (Gacutil.exe),](../tools/gacutil-exe-gac-tool.md) yalnızca dosya sürüm numarası daha yeni olduğunda bir derlemeyi değiştirmenize olanak tanır. Montajcı genellikle montaj sürüm numarası daha büyük olmadığı sürece bir derleme üzerine yüklemez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yan Yana Yürütme](side-by-side-execution.md)
- [Nasıl yapılır: Otomatik Bağlama Yönlendirmesini Etkinleştirme veya Devre Dışı Bırakma](../configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)
