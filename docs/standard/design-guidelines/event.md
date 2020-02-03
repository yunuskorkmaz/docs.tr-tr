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
ms.openlocfilehash: b44ee5933f8629b4dddbf3be1b79b2e77b0254f7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741679"
---
# <a name="event-design"></a>Olay Tasarımı
Olaylar en yaygın olarak kullanılan geri çağırma biçimidir (Framework 'ün Kullanıcı koduna çağrı yapmasına izin veren yapılar). Diğer geri çağırma mekanizmaları, temsilciler, sanal üyeler ve arabirim tabanlı eklentiler alan üyeleri içerir. kullanılabilirlik çalışmalarından veriler, geliştiricilerin büyük bir bölümünün diğer geri çağırma mekanizmalarını kullandıklarından daha rahat olduğunu belirtir . Olaylar, Visual Studio ve birçok dil ile tamamen tümleşiktir.

 İki olay grubu olduğunu unutmamak önemlidir: bir sistem değişikliği durumu, ön olaylar adı ve durum değişikliklerinden sonra oluşturulan olaylar, olaylar sonrası olarak adlandırılır. Bir form kapatılmadan önce oluşturulan `Form.Closing`ön olaya bir örnektir. Bir form kapatıldıktan sonra oluşturulan olay sonrası `Form.Closed`bir örnektir.

 ✔️ "yangın" veya "tetikleyici" yerine olaylar için "Raise" terimini kullanır.

 ✔️ olay işleyicileri olarak kullanılacak yeni temsilciler el ile oluşturmak yerine <xref:System.EventHandler%601?displayProperty=nameWithType> kullanın.

 ✔️, olayın olay işleme yöntemine hiçbir şekilde herhangi bir veri taşıması gerekmeyeceğinden kesinlikle emin olmadığınız sürece, olay bağımsız değişkeni olarak <xref:System.EventArgs> bir alt sınıfını kullanmayı düşünün. Bu durumda, `EventArgs` türünü doğrudan kullanabilirsiniz.

 Doğrudan `EventArgs` kullanarak bir API dağıtırsanız, hiçbir veri, hiçbir şekilde, hiçbir verileri hiçbir şekilde uyumluluk olmadan bu olayla birlikte ekleyemezsiniz. Bir alt sınıf kullanırsanız, başlangıçta tamamen boş olsalar bile, gerektiğinde alt sınıfa özellikler ekleyebilirsiniz.

 ✔️ her olayı yükseltmek için korumalı bir sanal yöntem kullanın. Bu yalnızca korumasız sınıflarda, yapıları, mühürlü sınıfları veya statik olayları değil, statik olmayan olaylar için geçerlidir.

 Yönteminin amacı, bir geçersiz kılma kullanarak bir türetilmiş sınıfın olayı işlemesi için bir yol sağlamaktır. Geçersiz kılma türetilmiş sınıflarda temel sınıf olaylarını işlemek için daha esnek, daha hızlı ve daha doğal bir yoldur. Kurala göre, yöntemin adı "on" ile başlamalı ve bunun ardından olayın adı gelmelidir.

 Türetilmiş sınıf, geçersiz kılma içindeki yöntemin temel uygulamasını çağırmamalıdır. Temel sınıfın düzgün çalışması için gerekli olan yöntemde herhangi bir işlem dahil edilmez, bunun için hazırlıklı olun.

 ✔️, bir olayı başlatan korumalı yönteme tek bir parametre alır.

 Parametresi `e` olarak adlandırılmalıdır ve olay bağımsız değişkeni sınıfı olarak yazılmalıdır.

 statik olmayan bir olay oluşturulurken ❌ gönderen olarak null geçirmeyin.

 statik bir olay oluştururken ✔️ gönderen olarak null geçirin.

 ❌ bir olayı oluştururken olay verileri parametresi olarak null geçirmeyin.

 Herhangi bir veriyi olay işleme yöntemine geçirmek istemiyorsanız `EventArgs.Empty` geçirmeniz gerekir. Geliştiriciler bu parametrenin null olmasını bekler.

 ✔️ Son kullanıcının iptal edebilmesini sağlayan olayları kullanmayı düşünün. Bu yalnızca ön olaylar için geçerlidir.

 Son kullanıcının olayları iptal edebilmesini sağlamak için olay bağımsız değişkeni olarak <xref:System.ComponentModel.CancelEventArgs?displayProperty=nameWithType> veya alt sınıfını kullanın.

### <a name="custom-event-handler-design"></a>Özel olay Işleyicisi tasarımı
 Framework 'ün, genel türleri desteklemeyen CLR 'nin önceki sürümleriyle çalışması gerektiği durumlar gibi `EventHandler<T>` kullanılamaz. Bu gibi durumlarda, özel bir olay işleyicisi temsilcisi tasarlamanızı ve geliştirmeniz gerekebilir.

 ✔️ olay işleyicileri için void dönüş türü kullanın.

 Bir olay işleyicisi, muhtemelen birden çok nesnede çok sayıda olay işleme yöntemini çağırabilir. Olay işleme yöntemlerinin bir değer döndürmesine izin veriliyorsa, her olay çağrısı için birden fazla dönüş değeri olacaktır.

 ✔️ olay işleyicisinin ilk parametresinin türü olarak `object` kullanın ve `sender`çağırır.

 ✔️ <xref:System.EventArgs?displayProperty=nameWithType> veya alt sınıfını olay işleyicisinin ikinci parametresinin türü olarak kullanın ve `e`çağırın.

 ❌ olay işleyicilerinde ikiden fazla parametre yok.

 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*

 *, Microsoft Windows geliştirme serisinin bir parçası olarak, [.NET kitaplıkları için 2. sürüm](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vazysztof Cwalina ve atacan Abk2008 MS, 4. Adım: Addison-Wesley Professional tarafından yeniden yazdırılmıştır.*

## <a name="see-also"></a>Ayrıca bkz.

- [Üye Tasarımı Yönergeleri](../../../docs/standard/design-guidelines/member.md)
- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
