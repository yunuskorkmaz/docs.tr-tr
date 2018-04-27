---
title: Oluşturucu tasarım
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- member design guidelines, constructors
- constructors, design guidelines
- instance constructors
- type constructors
- virtual members
- constructors, types
- default constructors
- static constructors
ms.assetid: b4496afe-5fa7-4bb0-85ca-70b0ef21e6fc
caps.latest.revision: 12
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d208511bd04d5daf9930ecf6cf53e7708ca4da3f
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
---
# <a name="constructor-design"></a>Oluşturucu tasarım
Oluşturucular iki tür vardır: oluşturucular ve örnek oluşturucuları yazın.  
  
 Türü oluşturucuları statik ve CLR tarafından türü kullanılmadan önce çalıştırılır. Örnek oluşturucuları bir türünün bir örneği oluşturulduğunda çalıştırın.  
  
 Türü oluşturucuları parametreleri alamıyor. Örnek oluşturucuları olabilir. Herhangi bir parametre ele yok örnek oluşturucuları genellikle varsayılan oluşturucular denir.  
  
 Oluşturucular bir türün örneklerinin oluşturmak için en iyi yoludur. Çoğu geliştirici arayın ve örnekler (örneğin, Fabrika yöntemleri) oluşturma alternatif yolu düşünmeden önce bir oluşturucu kullanmayı deneyin.  
  
 **✓ DÜŞÜNÜN** sağlayan basit, ideal olarak varsayılan, Oluşturucular.  
  
 Parametreler çok az sayıda basit bir oluşturucuya sahip ve tüm ilkel veya numaralandırmaları parametreleridir. Bu tür basit oluşturucular framework kullanılabilirliğini artırın.  
  
 **✓ DÜŞÜNÜN** statik Üreteç yöntemi yerine bir oluşturucu istenen işlemin semantiği doğrudan yapımı yeni bir örneğini eşleşmiyorsa ya da Oluşturucusu tasarım yönergeleri izleyerek doğal olmayan hissi kullanarak.  
  
 **✓ YAPMAK** ana özelliklerini ayarlamak için kısayol olarak Oluşturucusu parametrelerini kullanın.  
  
 Semantiği fark olmalıdır bazı özellik kümeleri tarafından izlenen boş Oluşturucusu kullanma ve birden çok bağımsız değişkenlerle bir oluşturucu kullanma.  
  
 **✓ YAPMAK** Oluşturucu parametreleri yalnızca özelliğini ayarlamak için kullanılan Oluşturucu parametreleri ve bir özellik için aynı adı kullanın.  
  
 Tür parametreleri ve özellikleri arasındaki tek fark büyük/küçük harfleri.  
  
 **✓ YAPMAK** Oluşturucusu en az iş.  
  
 Oluşturucular kadar iş yakalama dışında Oluşturucu parametreleri yapmanız gerekir. Başka bir işlem maliyetini gerekli kadar Gecikmeli.  
  
 **✓ YAPMAK** uygunsa örnek Oluşturucular, özel durumlar oluşturma.  
  
 **✓ YAPMAK** böyle bir oluşturucu gerekliyse, sınıflar, bir ortak varsayılan oluşturucu açıkça bildirin.  
  
 Bir türde tüm oluşturucular açıkça bildirmeyin, birçok dilde (örneğin, C# ' ta) otomatik olarak ortak varsayılan bir oluşturucu ekleyin. (Soyut sınıflar korumalı Oluşturucu Al)  
  
 Parametreli oluşturucusu için sınıf ekleme derleyici varsayılan oluşturucu eklemesini engeller. Bu genellikle yanlışlıkla önemli değişiklikler neden olur.  
  
 **KAÇININ x** açıkça varsayılan oluşturucular üzerinde yapıları tanımlama.  
  
 Varsayılan Oluşturucu tanımlanmazsa, bu dizinin her bir yuvada çalıştırılacak sahip olmadığından bu dizi oluşturma daha hızlı hale getirir. C# ' de dahil olmak üzere birçok derleyicileri, bu nedenle parametresiz kurucular yapılar izin verme unutmayın.  
  
 **KAÇININ x** kurucusu içinde bir nesne üzerinde sanal üyeler çağırma.  
  
 En çok türetilen Tür oluşturucu tam henüz çalıştırılmadı olsa bile sanal üyesi çağırma çağrılacak, en çok türetilen override neden olur.  
  
### <a name="type-constructor-guidelines"></a>Türü kurucusunu yönergeleri  
 **✓ YAPMAK** statik oluşturucular özel yap.  
  
 Bir sınıf oluşturucu olarak da adlandırılan bir statik Oluşturucu türü başlatmak için kullanılır. CLR türünün ilk örneği oluşturulduğunda veya ilgili türdeki tüm statik üyeler denir önce statik Oluşturucusu çağırır. Kullanıcının statik Oluşturucusu ne zaman çağrıldığını üzerinde denetimi yoktur. Statik oluşturucu özel durumda değilse, CLR dışında bir kod tarafından çağrılabilir. Oluşturucuda gerçekleştirilen işlemler bağlı olarak bu beklenmeyen davranışlara neden olabilir. C# Derleyici statik oluşturucular özel olmasını zorlar.  
  
 **X yok** statik oluşturucular özel durumlar oluşturma.  
  
 Bir özel durum türü oluşturucudan oluşturulursa türü geçerli uygulama etki alanında kullanılabilir değil.  
  
 **✓ DÜŞÜNÜN** çalışma zamanı açıkça tanımlanmış bir statik oluşturucusu yok türleri performansını optimize etmek mümkün olduğundan statik oluşturucular açıkça kullanmak yerine statik alanları satır içi başlatılıyor.  
  
 *Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Üye Tasarımı Yönergeleri](../../../docs/standard/design-guidelines/member.md)  
 [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
