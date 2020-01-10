---
title: Olay Tasarımı
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- pre-events
- events [.NET Framework], design guidelines
- member design guidelines, events
- event handlers [.NET Framework], event design guidelines
- post-events
- signatures, event handling
ms.assetid: 67b3c6e2-6a8f-480d-a78f-ebeeaca1b95a
ms.openlocfilehash: 78d765a7af77b1e6a6ecd483677cea2d4c6b0d5b
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709432"
---
# <a name="event-design"></a>Olay Tasarımı
Olaylar en yaygın olarak kullanılan geri çağırma biçimidir (Framework 'ün Kullanıcı koduna çağrı yapmasına izin veren yapılar). Diğer geri çağırma mekanizmaları, temsilciler, sanal üyeler ve arabirim tabanlı eklentiler alan üyeleri içerir. kullanılabilirlik çalışmalarından veriler, geliştiricilerin büyük bir bölümünün diğer geri çağırma mekanizmalarını kullandıklarından daha rahat olduğunu belirtir . Olaylar, Visual Studio ve birçok dil ile tamamen tümleşiktir.  
  
 İki olay grubu olduğunu unutmamak önemlidir: bir sistem değişikliği durumu, ön olaylar adı ve durum değişikliklerinden sonra oluşturulan olaylar, olaylar sonrası olarak adlandırılır. Bir form kapatılmadan önce oluşturulan `Form.Closing`ön olaya bir örnektir. Bir form kapatıldıktan sonra oluşturulan olay sonrası `Form.Closed`bir örnektir.  
  
 **✓ DO** olayları yerine "yangın" veya "tetikleyicisi." için "Oluştur" terimi kullanın  
  
 **✓ DO** kullanmak <xref:System.EventHandler%601?displayProperty=nameWithType> el ile olay işleyicileri olarak kullanılacak yeni temsilciler oluşturmak yerine.  
  
 **✓ CONSIDER** öğesinin bir alt kümesi kullanarak <xref:System.EventArgs> olay bağımsız değişken olarak olay olay yöntemi, işleme için herhangi bir veri taşımak hiçbir zaman gerekir kesinlikle emin olmadığınız sürece bu durumda kullanabilirsiniz `EventArgs` doğrudan yazın.  
  
 Doğrudan `EventArgs` kullanarak bir API dağıtırsanız, hiçbir veri, hiçbir şekilde, hiçbir verileri hiçbir şekilde uyumluluk olmadan bu olayla birlikte ekleyemezsiniz. Bir alt sınıf kullanırsanız, başlangıçta tamamen boş olsalar bile, gerektiğinde alt sınıfa özellikler ekleyebilirsiniz.  
  
 **✓ DO** her olay oluşturmak için korumalı sanal bir yöntem kullanın. Bu yalnızca korumasız sınıflarda, yapıları, mühürlü sınıfları veya statik olayları değil, statik olmayan olaylar için geçerlidir.  
  
 Yönteminin amacı, bir geçersiz kılma kullanarak bir türetilmiş sınıfın olayı işlemesi için bir yol sağlamaktır. Geçersiz kılma türetilmiş sınıflarda temel sınıf olaylarını işlemek için daha esnek, daha hızlı ve daha doğal bir yoldur. Kurala göre, yöntemin adı "on" ile başlamalı ve bunun ardından olayın adı gelmelidir.  
  
 Türetilmiş sınıf, geçersiz kılma içindeki yöntemin temel uygulamasını çağırmamalıdır. Temel sınıfın düzgün çalışması için gerekli olan yöntemde herhangi bir işlem dahil edilmez, bunun için hazırlıklı olun.  
  
 **✓ DO** bir olay başlatır korumalı yöntemi için tek bir parametre almalıdır.  
  
 Parametresi `e` olarak adlandırılmalıdır ve olay bağımsız değişkeni sınıfı olarak yazılmalıdır.  
  
 **X DO NOT** statik olmayan bir olayı tetiklenmeden olduğunda gönderen olarak null geçir.  
  
 **✓ DO** statik olayı tetiklenmeden olduğunda gönderen olarak null geçir.  
  
 **X DO NOT** bir olayı tetiklenmeden olduğunda olay verileri parametre null geçir.  
  
 Herhangi bir veriyi olay işleme yöntemine geçirmek istemiyorsanız `EventArgs.Empty` geçirmeniz gerekir. Geliştiriciler bu parametrenin null olmasını bekler.  
  
 **✓ CONSIDER** son kullanıcı iptal edebilirsiniz olaylar oluşturma. Bu yalnızca ön olaylar için geçerlidir.  
  
 Son kullanıcının olayları iptal edebilmesini sağlamak için olay bağımsız değişkeni olarak <xref:System.ComponentModel.CancelEventArgs?displayProperty=nameWithType> veya alt sınıfını kullanın.  
  
### <a name="custom-event-handler-design"></a>Özel olay Işleyicisi tasarımı  
 Framework 'ün, genel türleri desteklemeyen CLR 'nin önceki sürümleriyle çalışması gerektiği durumlar gibi `EventHandler<T>` kullanılamaz. Bu gibi durumlarda, özel bir olay işleyicisi temsilcisi tasarlamanızı ve geliştirmeniz gerekebilir.  
  
 **✓ DO** dönüş türü void olay işleyicileri için kullanın.  
  
 Bir olay işleyicisi, muhtemelen birden çok nesnede çok sayıda olay işleme yöntemini çağırabilir. Olay işleme yöntemlerinin bir değer döndürmesine izin veriliyorsa, her olay çağrısı için birden fazla dönüş değeri olacaktır.  
  
 **✓ DO** kullanmak `object` olay işleyicisinin ilk parametresinin türü olarak ve çağrısından `sender`.  
  
 **✓ DO** kullanmak <xref:System.EventArgs?displayProperty=nameWithType> veya onun bir alt olay işleyicisinin ikinci parametrenin türü olarak ve çağrısından `e`.  
  
 **X DO NOT** olay işleyicileri ikiden fazla parametrelere sahip.  
  
 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Üye Tasarımı Yönergeleri](../../../docs/standard/design-guidelines/member.md)
- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
