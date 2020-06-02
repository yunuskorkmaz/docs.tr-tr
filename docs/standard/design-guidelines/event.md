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
ms.openlocfilehash: 852c99b1a41691911f7ae82d3b8104526811757d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289830"
---
# <a name="event-design"></a>Olay Tasarımı
Olaylar en yaygın olarak kullanılan geri çağırma biçimidir (Framework 'ün Kullanıcı koduna çağrı yapmasına izin veren yapılar). Diğer geri çağırma mekanizmaları, temsilciler, sanal üyeler ve arabirim tabanlı eklentiler alan üyeleri içerir. kullanılabilirlik çalışmalarından veriler, geliştiricilerin büyük bölümünün diğer geri çağırma mekanizmalarını kullandıklarından daha rahat olduğunu gösterir. Olaylar, Visual Studio ve birçok dil ile tamamen tümleşiktir.

 İki olay grubu olduğunu unutmamak önemlidir: bir sistem değişikliği durumu, ön olaylar adı ve durum değişikliklerinden sonra oluşturulan olaylar, olaylar sonrası olarak adlandırılır. Bir form kapatılmadan önce oluşturulan bir ön olaya bir örnek olabilir `Form.Closing` . Bir form kapatıldıktan sonra oluşturulan olay sonrası bir örnek olabilir `Form.Closed` .

 ✔️ "yangın" veya "tetikleyici" yerine olaylar için "Raise" terimini kullanır.

 <xref:System.EventHandler%601?displayProperty=nameWithType>olay işleyicileri olarak kullanılacak yeni temsilcileri el ile oluşturmak yerine ✔️ kullanın.

 ✔️ olay <xref:System.EventArgs> işleme yöntemine herhangi bir veriyi hiçbir şekilde hiçbir şekilde hiçbir şekilde bir veri taşıması gerekmeyeceğinden emin olmadığınız sürece, türü doğrudan kullanabilmeniz için olay bağımsız değişkeni olarak ' ın bir alt sınıfını KULLANMAYı düşünün `EventArgs` .

 Doğrudan kullanarak bir API 'yi dağıtırsanız `EventArgs` , hiçbir veri, hiçbir hiçbir veriyi hiçbir şekilde uyumluluk olmadan, olayla birlikte hiçbir hiçbir şekilde ekleyemeyeceksiniz. Bir alt sınıf kullanırsanız, başlangıçta tamamen boş olsalar bile, gerektiğinde alt sınıfa özellikler ekleyebilirsiniz.

 ✔️ her olayı yükseltmek için korumalı bir sanal yöntem kullanın. Bu yalnızca korumasız sınıflarda, yapıları, mühürlü sınıfları veya statik olayları değil, statik olmayan olaylar için geçerlidir.

 Yönteminin amacı, bir geçersiz kılma kullanarak bir türetilmiş sınıfın olayı işlemesi için bir yol sağlamaktır. Geçersiz kılma türetilmiş sınıflarda temel sınıf olaylarını işlemek için daha esnek, daha hızlı ve daha doğal bir yoldur. Kurala göre, yöntemin adı "on" ile başlamalı ve bunun ardından olayın adı gelmelidir.

 Türetilmiş sınıf, geçersiz kılma içindeki yöntemin temel uygulamasını çağırmamalıdır. Temel sınıfın düzgün çalışması için gerekli olan yöntemde herhangi bir işlem dahil edilmez, bunun için hazırlıklı olun.

 ✔️, bir olayı başlatan korumalı yönteme tek bir parametre alır.

 Parametrenin adlandırılması `e` ve olay bağımsız değişkeni sınıfı olarak yazılması gerekir.

 ❌Statik olmayan bir olay oluşturulurken Gönderici olarak null geçirmeyin.

 statik bir olay oluştururken ✔️ gönderen olarak null geçirin.

 ❌Bir olayı oluştururken olay verileri parametresi olarak null geçirmeyin.

 `EventArgs.Empty`Herhangi bir veriyi olay işleme yöntemine geçirmek istemiyorsanız, geçişi yapmalısınız. Geliştiriciler bu parametrenin null olmasını bekler.

 ✔️ Son kullanıcının iptal edebilmesini sağlayan olayları kullanmayı düşünün. Bu yalnızca ön olaylar için geçerlidir.

 <xref:System.ComponentModel.CancelEventArgs?displayProperty=nameWithType>Son kullanıcının olayları iptal edebilmesini sağlamak için olay bağımsız değişkeni olarak veya alt sınıfını kullanın.

### <a name="custom-event-handler-design"></a>Özel olay Işleyicisi tasarımı
 `EventHandler<T>`Çerçevenin, genel türleri DESTEKLEMEYEN clr 'nin önceki sürümleriyle çalışması gerektiğinde olduğu gibi, kullanılamayan durumlar vardır. Bu gibi durumlarda, özel bir olay işleyicisi temsilcisi tasarlamanızı ve geliştirmeniz gerekebilir.

 ✔️ olay işleyicileri için void dönüş türü kullanın.

 Bir olay işleyicisi, muhtemelen birden çok nesnede çok sayıda olay işleme yöntemini çağırabilir. Olay işleme yöntemlerinin bir değer döndürmesine izin veriliyorsa, her olay çağrısı için birden fazla dönüş değeri olacaktır.

 ✔️ `object` olay işleyicisinin ilk parametresinin türü olarak kullanın ve bunu çağırın `sender` .

 ✔️ <xref:System.EventArgs?displayProperty=nameWithType> veya alt sınıfını olay işleyicisinin ikinci parametresinin türü olarak kullanın ve çağırın `e` .

 ❌Olay işleyicilerinde ikiden fazla parametre yok.

 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*

 *, Microsoft Windows geliştirme serisinin bir parçası olarak, [.NET kitaplıkları için 2. sürüm](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vazysztof Cwalina ve atacan Abk2008 MS, 4. Adım: Addison-Wesley Professional tarafından yeniden yazdırılmıştır.*

## <a name="see-also"></a>Ayrıca bkz.

- [Üye tasarımı yönergeleri](member.md)
- [Çerçeve tasarım yönergeleri](index.md)
