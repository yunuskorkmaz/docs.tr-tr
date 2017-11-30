---
title: "Uzantı Metotları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5de945cb-88f4-49d7-b0e6-f098300cf357
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b7edc3420eabe4de20a2fe39f38ae5eee53b593c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="extension-methods"></a>Uzantı Metotları
Genişletme yöntemleri örnek yöntemi çağrı sözdizimini kullanarak çağrılması için statik yöntemler sağlayan bir dil özelliğidir. Bu yöntemler üzerinde çalışılacak yöntemdir örneğini gösteren en az bir parametre almalıdır.  
  
 Bu tür genişletme yöntemlerini açıklar sınıfı "sponsoru" sınıf olarak adlandırılır ve static olarak bildirilmelidir. Genişletme yöntemleri kullanmak için bir sponsoru sınıfı tanımlayan ad alanı almanız gerekir.  
  
 **KAÇININ x** frivolously genişletme yöntemleri, özellikle yok kendi türlerinde tanımlama.  
  
 Kaynak kodu türü sahipseniz, normal örnek yöntemleri kullanmayı düşünün. Size ait olmayan ve bir yöntem eklemek istiyorsanız, çok dikkatli olun. Genişletme yöntemleri serbest kullanımını API'leri bu yöntemleri için tasarlanmamıştır türlerinin alanınızda karışıklık, olasılığı vardır.  
  
 **✓ DÜŞÜNÜN** genişletme yöntemleri aşağıdaki senaryolardan birini kullanarak:  
  
-   Yardımcı sağlamak için işlevselliği denirse, ilgili her bir arabirim uygulama için işlevselliği açısından çekirdek arabirimi yazılabilir. Somut uygulamaları aksi arabirimlerine atanamaz olmasıdır. Örneğin, `LINQ to Objects` işleçleri uzantı yöntemleri olarak tüm uygulanır <xref:System.Collections.Generic.IEnumerable%601> türleri. Bu nedenle, herhangi bir `IEnumerable<>` otomatik olarak LINQ etkin uygulamasıdır.  
  
-   Bir bağımlılık bazı türünde, ancak böyle bir bağımlılık örnek yöntemi zaman gösterebileceği bağımlılık Yönetimi kurallarını çalışmamasına neden. Örneğin, bir bağımlılık <xref:System.String> için <xref:System.Uri?displayProperty=nameWithType> arzu, büyük olasılıkla değil ve bu nedenle `String.ToUri()` döndüren örnek yöntemi `System.Uri` bağımlılık yönetim açısından yanlış tasarım olacaktır. Statik genişletme yöntemi `Uri.ToUri(this string str)` döndüren `System.Uri` kadar daha iyi tasarım olacaktır.  
  
 **KAÇININ x** üzerinde genişletme yöntemleri tanımlama <xref:System.Object?displayProperty=nameWithType>.  
  
 VB kullanıcılar tür yöntem uzantı yöntemi sözdizimini kullanarak nesne başvuruları üzerinde arayabilmesi için olmayacaktır. VB VB içinde nesne üzerinde geç olması için tüm yöntem çağrılarına zorlar gibi bir başvuru bildirme bağlı olduğundan, bu tür yöntemleri çağırma desteklemez (gerçek üye adlı çalışma zamanında belirlenir) bağlamaları genişletme yöntemleri için derleme zamanında (erken belirlenen sırada bağlı).  
  
 Kılavuz aynı bağlama davranışı mevcut olduğu veya nerede genişletme yöntemleri desteklenmez diğer diller için geçerli olduğunu unutmayın.  
  
 **X yok** veya bağımlılık yönetimi yöntemleri arabirimlerine ekleme için olmadığı sürece, genişletilmiş türü aynı ad alanına genişletme yöntemleri uygulamak.  
  
 **KAÇININ x** farklı ad alanlarında bulunuyorsa bile aynı imzayla iki veya daha fazla genişletme yöntemleri tanımlama.  
  
 **✓ DÜŞÜNÜN** türü bir arabirim ise ve çoğu veya tamamı durumlarda kullanılacak genişletme yöntemleri istediyseniz genişletilmiş türü olarak aynı ad alanında genişletme yöntemleri tanımlama.  
  
 **X yok** normalde diğer özelliklerle ilişkili ad alanlarında bir özellik uygulama uzantı yöntemleri tanımlar. Bunun yerine, bunları ait özelliğiyle ilgili ad alanını tanımlayın.  
  
 **KAÇININ x** genel bir ad alanları adlandırma ayrılmış genişletme yöntemleri (örneğin, "uzantılarla"). Açıklayıcı bir ad kullanın (örneğin, "yönlendirme") yerine.  
  
 *Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Üye tasarım yönergeleri](../../../docs/standard/design-guidelines/member.md)  
 [Framework tasarım yönergeleri](../../../docs/standard/design-guidelines/index.md)
