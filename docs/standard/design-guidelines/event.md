---
title: Olay tasarımı
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- pre-events
- events [.NET Framework], design guidelines
- member design guidelines, events
- event handlers [.NET Framework], event design guidelines
- post-events
- signatures, event handling
ms.assetid: 67b3c6e2-6a8f-480d-a78f-ebeeaca1b95a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b257da73d33fae54ef464e9dd69906316b87fd88
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2018
ms.locfileid: "44709706"
---
# <a name="event-design"></a>Olay tasarımı
Olayları en yaygın kullanılan geri çağırmalar (kullanıcı koda çağrı için framework izin yapıları) biçimindedir. Başka bir geri çağırma mekanizmalar Temsilciler, sanal üyeleri ve arabirim tabanlı eklentileri alma üyeleri içerir. Kullanılabilirlik incelemeleri verilerden geliştiricilerin çoğu kullandıkları için bir geri çağırma mekanizmaları çok olayları kullanarak daha iyi olduğunu gösterir. Olayları Visual Studio ve birçok dili ile sorunsuz şekilde tümleşiktir.  
  
 İki olay gruplarını olduğuna dikkat edin önemlidir: öncesi olayları ve bir durum olarak değiştirdikten sonra oluşturulan olayları adlı Sistem değişiklikleri durumunu önce harekete geçirilen olayları sonrası olayları çağrılır. Bir ön olayının örnek verilebilir `Form.Closing`, bir form kapatılmadan hemen önce oluşturulur. Örnek sonrası olayının `Form.Closed`, bir form kapatıldıktan sonra oluşturulur.  
  
 **✓ DO** olayları yerine "yangın" veya "tetikleyicisi." için "Oluştur" terimi kullanın  
  
 **✓ DO** kullanmak <xref:System.EventHandler%601?displayProperty=nameWithType> el ile olay işleyicileri olarak kullanılacak yeni temsilciler oluşturmak yerine.  
  
 **✓ CONSIDER** öğesinin bir alt kümesi kullanarak <xref:System.EventArgs> olay bağımsız değişken olarak olay olay yöntemi, işleme için herhangi bir veri taşımak hiçbir zaman gerekir kesinlikle emin olmadığınız sürece bu durumda kullanabilirsiniz `EventArgs` doğrudan yazın.  
  
 Bir API'yi kullanarak gönderdiğimde `EventArgs` doğrudan, hiç olay ile uyumluluk bozup olmadan gerçekleştirilmesi için herhangi bir veri eklemek mümkün olmayacak. Öğesinin alt sınıfı kullanırsanız, hatta başlangıçta tamamen boş, gerektiğinde alt özellikler eklemeniz mümkün olmayacak durumunda.  
  
 **✓ DO** her olay oluşturmak için korumalı sanal bir yöntem kullanın. Bu durum yalnızca statik olmayan olayları mühürsüz sınıflar, yapılar, sınıfları veya statik olaylar için geçerlidir.  
  
 Yöntem amacı, bir geçersiz kılma kullanılarak olayı işlemek bir türetilen sınıf için bir yol sağlamaktır. Geçersiz kılma türetilmiş sınıflarda temel sınıf olayları işlemek için daha esnek, daha hızlı ve daha doğal bir yoludur. Kural olarak, yöntemin adı "ile" başlatmak ve olay adıyla izlenmesi.  
  
 Türetilmiş sınıf, yöntemin taban uygulamasını kendi geçersiz kılma seçeneğinde çağırmamanız seçebilirsiniz. Bu, herhangi bir işlem düzgün çalışması temel sınıf için gerekli olan yönteminde içermeden tarafından hazır olun.  
  
 **✓ DO** bir olay başlatır korumalı yöntemi için tek bir parametre almalıdır.  
  
 Parametre adlı `e` ve olay bağımsız değişken sınıf olarak yazılmalıdır.  
  
 **X DO NOT** statik olmayan bir olayı tetiklenmeden olduğunda gönderen olarak null geçir.  
  
 **✓ DO** statik olayı tetiklenmeden olduğunda gönderen olarak null geçir.  
  
 **X DO NOT** bir olayı tetiklenmeden olduğunda olay verileri parametre null geçir.  
  
 Geçirmeniz `EventArgs.Empty` olay yöntemi işleme için herhangi bir veri geçirmek istemiyorsanız. Geliştiriciler bu parametre null olmaması beklenir.  
  
 **✓ CONSIDER** son kullanıcı iptal edebilirsiniz olaylar oluşturma. Bu, yalnızca öncesi olaylar için geçerlidir.  
  
 Kullanım <xref:System.ComponentModel.CancelEventArgs?displayProperty=nameWithType> veya onun alt olayları iptal etmek son kullanıcı izin vermek için olay bağımsız değişkeni olarak.  
  
### <a name="custom-event-handler-design"></a>Özel olay işleyicisi tasarım  
 Hangi durumlarda vardır `EventHandler<T>` Framework'te genel türler desteklememektedir CLR'nin önceki sürümleriyle çalışmaya gerektiğinde gibi kullanılamaz. Böyle durumlarda bir özel olay işleyici temsilcisini tasarlayıp gerekebilir.  
  
 **✓ DO** dönüş türü void olay işleyicileri için kullanın.  
  
 Bir olay işleyicisi, birden çok olay işleme, birden çok nesnelerde yöntemi çağırabilirsiniz. Bir değer döndürmek için olay işleme yöntemleri izin verilirse, her olay çağırma için birden çok değer olacaktır.  
  
 **✓ DO** kullanmak `object` olay işleyicisinin ilk parametresinin türü olarak ve çağrısından `sender`.  
  
 **✓ DO** kullanmak <xref:System.EventArgs?displayProperty=nameWithType> veya onun bir alt olay işleyicisinin ikinci parametrenin türü olarak ve çağrısından `e`.  
  
 **X DO NOT** olay işleyicileri ikiden fazla parametrelere sahip.  
  
 *Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Üye Tasarımı Yönergeleri](../../../docs/standard/design-guidelines/member.md)  
- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
