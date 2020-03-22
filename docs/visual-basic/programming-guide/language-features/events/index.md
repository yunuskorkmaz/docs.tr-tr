---
title: Olaylar
ms.date: 07/20/2015
helpviewer_keywords:
- events [Visual Basic], about events
- events [Visual Basic]
ms.assetid: 8fb0353a-e41b-4e23-b78f-da65db832f70
ms.openlocfilehash: 666e138a747c480ef9e8b593f8c6233105fcdc93
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400843"
---
# <a name="events-visual-basic"></a>Olaylar (Visual Basic)
Bir Visual Studio projesini bir dizi yordam olarak görselleştirebilirsiniz, gerçekte, çoğu program olay odaklıdır- yani yürütme akışı *olaylar*adı verilen dış olaylartarafından belirlenir.  
  
 Olay, bir uygulamaya önemli bir şeyin meydana geldiğini bildiren bir sinyaldir. Örneğin, bir kullanıcı formdaki denetimi tıklattığında, form bir `Click` olayı yükseltebilir ve olayı işleyen bir yordam çağırabilir. Olaylar da ayrı görevlerin iletişim kurmasına izin verir. Örneğin, uygulamanızın ana uygulamadan ayrı bir sıralama görevi gerçekleştirdiğini söyleyin. Bir kullanıcı sıralamayı iptal ederse, uygulamanız sıralama işleminin durdurulmasını sağlayan bir iptal olayı gönderebilir.  
  
## <a name="event-terms-and-concepts"></a>Etkinlik Terimleri ve Kavramları  
 Bu bölümde Visual Basic'te olaylarla birlikte kullanılan terim ve kavramlar açıklanmaktadır.  
  
### <a name="declaring-events"></a>Olayları Bildirme  
 Aşağıdaki örnekte olduğu gibi, anahtar kelimeyi `Event` kullanarak sınıflar, yapılar, modüller ve arabirimler deki olayları bildirirsiniz:  
  
 [!code-vb[VbVbalrEvents#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#24)]  
  
### <a name="raising-events"></a>Yetiştirme Etkinlikleri  
 Olay, önemli bir şeyin gerçekleştiğini bildiren bir ileti gibidir. İletiyi yayınlama eylemine olayı *yükseltme* denir. Visual Basic'te, aşağıdaki `RaiseEvent` örnekte olduğu gibi olayları deyimle yükseltirsiniz:  
  
 [!code-vb[VbVbalrEvents#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#25)]  
  
 Olaylar, sınıf, modül veya beyan edildikleri yapı kapsamında yükseltilmelidir. Örneğin, türetilmiş bir sınıf, taban sınıftan devralınan olayları kaldıramaz.  
  
### <a name="event-senders"></a>Olay Gönderenler  
 Bir olayı yükseltebilen herhangi bir nesne, olay *kaynağı*olarak da bilinen bir *olay gönderendir.* Formlar, denetimler ve kullanıcı tanımlı nesneler olay gönderenlere örnektir.  
  
### <a name="event-handlers"></a>Olay İşleyicileri  
 *Olay işleyicileri,* karşılık gelen bir olay oluştuğunda çağrılan yordamlardır. Olay işleyicisi olarak eşleşen imzaiçeren geçerli bir alt yordam ı kullanabilirsiniz. Ancak, olay kaynağına bir değer döndüremekten sonra bir işlevi olay işleyicisi olarak kullanamazsınız.  
  
 Visual Basic, olay gönderenin adını, alt çiziyi ve olayın adını birleştiren olay işleyicileri için standart bir adlandırma kuralı kullanır. Örneğin, adlı `Click` `button1` bir düğmenin olayı `Sub button1_Click`adlandırılacak.  
  
> [!NOTE]
> Kendi olaylarınız için olay işleyicileri tanımlarken bu adlandırma kuralını kullanmanızı öneririz, ancak gerekli değildir; herhangi bir geçerli alt yordam adı kullanabilirsiniz.  
  
## <a name="associating-events-with-event-handlers"></a>Etkinlikleri Etkinlik İşleyicileriyle Ilişkilendirme  
 Bir olay işleyicisi kullanılabilir hale gelmeden önce, önce `Handles` bir `AddHandler` olay la ilişkilendirmek gerekir ya da deyimi kullanarak.  
  
### <a name="withevents-and-the-handles-clause"></a>WithEvents ve Handles Yan tümcesi  
 `WithEvents` İfade ve `Handles` yan tümce, olay işleyicilerini belirtmenin açıklayıcı bir yolunu sağlar. `WithEvents` Anahtar kelimeyle birlikte bildirilen bir nesne tarafından yükseltilen `Handles` bir olay, aşağıdaki örnekte gösterildiği gibi, söz konusu olay için bir deyimle herhangi bir yordam tarafından işlenebilir:  
  
 [!code-vb[VbVbalrEvents#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#1)]  
  
 Deyim `WithEvents` ve `Handles` yan tümce genellikle olay işleyicileri için en iyi seçimdir, çünkü kullandıkları bildirimsel sözdizimi olay işlemeyi kodlamayı, okumayı ve hata ayıklamayı kolaylaştırır. Ancak, değişkenlerin kullanımına ilişkin aşağıdaki `WithEvents` sınırlamalara dikkat edin:  
  
- Bir `WithEvents` değişkeni nesne değişkeni olarak kullanamazsınız. Diğer bir diğer olarak, `Object`değişkeni bildirirken sınıf adını belirtmeniz gerekir.  
  
- Paylaşılan olaylar sınıf örneklerine bağlı olmadığından, `WithEvents` paylaşılan olayları bildirimsel olarak işlemek için kullanamazsınız. Benzer şekilde, `WithEvents` `Handles` bir `Structure`. Her iki durumda da, `AddHandler` bu olayları işlemek için deyimi kullanabilirsiniz.  
  
- `WithEvents` Değişken dizileri oluşturamazsınız.  
  
 `WithEvents`değişkenler, tek bir olay işleyicisinin bir veya daha fazla tür olayı veya aynı tür olayı işlemek için bir veya daha fazla olay işleyicisini işlemesine izin verir.  
  
 `Handles` Yan tümce, bir olayı bir olay işleyicisiyle ilişkilendirmek için standart bir yol olsa da, olayları derleme zamanında olay işleyicileriyle ilişkilendirmekle sınırlıdır.  
  
 Formlar veya denetimlerle ilişkili olaylar gibi bazı durumlarda Visual Basic boş bir olay işleyicisi otomatik olarak saplar ve bir olayla ilişkilendirir. Örneğin, tasarım modunda bir formdaki bir komut düğmesini çift tıklattığınızda, Visual Basic `WithEvents` aşağıdaki kodda olduğu gibi boş bir olay işleyicisi ve komut düğmesi için bir değişken oluşturur:  
  
 [!code-vb[VbVbalrEvents#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#26)]  
  
### <a name="addhandler-and-removehandler"></a>AddHandler ve RemoveHandler  
 İfade, `AddHandler` her ikiside de bir olay işleyicisi belirtmenize izin veren `Handles` yan tümceye benzer. Ancak, `AddHandler`, `RemoveHandler`kullanılan, dinamik olarak `Handles` eklemek, kaldırmak ve bir olay ile ilişkili olay işleyicisi değiştirmek için izin yan tümcesi daha büyük esneklik sağlar. Paylaşılan olayları veya olayları bir yapıdan işlemek istiyorsanız, bunu kullanmanız `AddHandler`gerekir.  
  
 `AddHandler`iki bağımsız değişken alır: denetim gibi bir olay gönderenden bir olayın adı ve bir temsilciye değer bürünen bir ifade. Deyim her zaman temsilciye bir başvuru `AddHandler`döndürdüğünde temsilci sınıfını açıkça belirtmeniz gerekmez. `AddressOf` Aşağıdaki örnek, bir olay işleyicisini bir nesne tarafından yükseltilen bir olayla ilişkilendirer:  
  
 [!code-vb[VbVbalrEvents#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#28)]  
  
 `RemoveHandler`, bir olayı olay işleyicisinden kesen, `AddHandler`aynı sözdizimini kullanır. Örnek:  
  
 [!code-vb[VbVbalrEvents#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#29)]  
  
 Aşağıdaki örnekte, bir olay işleyicisi bir olayla ilişkilendirilir ve olay yükseltilir. Olay işleyicisi olayı yakalar ve bir ileti görüntüler.  
  
 Sonra ilk olay işleyicisi kaldırılır ve farklı bir olay işleyicisi olay ile ilişkilidir. Olay yeniden yükseltildiğinde, farklı bir ileti görüntülenir.  
  
 Son olarak, ikinci olay işleyicisi kaldırılır ve olay üçüncü kez yükseltilir. Olayla ilişkili bir olay işleyicisi artık olmadığından, hiçbir işlem yapılmaz.  
  
 [!code-vb[VbVbalrEvents#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class2.vb#38)]  
  
## <a name="handling-events-inherited-from-a-base-class"></a>Taban Sınıftan Devralınan Olayları Işleme  
 *Türemiş sınıflar*(temel sınıftan özellikleri devralan sınıflar- `Handles MyBase` deyimi kullanarak taban sınıfları tarafından yükseltilen olayları işleyebilir.  
  
### <a name="to-handle-events-from-a-base-class"></a>Taban sınıftan olayları işlemek için  
  
- Olay işleyicisi yordamınızın bildirim `Handles MyBase.`satırına olay *adı* deyimi ekleyerek, *olay adının* işlediğiniz taban sınıftaki olayın adı olduğu türemiş sınıfta bir olay işleyicisi bildirin. Örnek:  
  
     [!code-vb[VbVbalrEvents#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#12)]  
  
## <a name="related-sections"></a>İlgili Bölümler  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[İzlenecek yol: Olay Bildirme ve Oluşturma](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md)|Bir sınıf için olayları nasıl beyan edin ve yükseltecek şekilde adım adım açıklama sağlar.|  
|[İzlenecek yol: Olayları İşleme](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)|Olay işleyici yordamı nasıl yazılsüreceğini gösterir.|  
|[Nasıl yapılır: Engellemekten Kaçınacak Şekilde Özel Olayları Bildirme](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)|Olay işleyicilerinin eşzamanlı olarak çağrılmasını sağlayan özel bir olayın nasıl tanımlaneceğini gösterir.|  
|[Nasıl yapılır: Bellekten Kazanacak Şekilde Özel Olayları Bildirme](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)|Yalnızca olay işlendiğinde bellek kullanan özel bir olayın nasıl tanımlanış edilebildiğini gösterir.|  
|[Visual Basic'de Devralınmış Olay İşleyicileri İle İlgili Sorun Giderme](../../../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)|Devralınan bileşenlerdeki olay işleyicileri ile ortaya çıkan yaygın sorunları listeler.|  
|[Olaylar](../../../../standard/events/index.md)|.NET Framework içindeki olay modeli için genel bir bakış sağlar.|  
|[Windows Forms'ta Olay İşleyicileri Oluşturma](../../../../framework/winforms/creating-event-handlers-in-windows-forms.md)|Windows Forms nesneleri ile ilişkili olaylarla nasıl çalışılabildiğini açıklar.|  
|[Temsilciler](../../../../visual-basic/programming-guide/language-features/delegates/index.md)|Visual Basic'te delegelere genel bir bakış sağlar.|
