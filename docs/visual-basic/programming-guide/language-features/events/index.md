---
title: Olaylar (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- events [Visual Basic], about events
- events [Visual Basic]
ms.assetid: 8fb0353a-e41b-4e23-b78f-da65db832f70
ms.openlocfilehash: 08bd3b3c7ff5608193de0cdc1a869e0918c9e96e
ms.sourcegitcommit: d9a0071d0fd490ae006c816f78a563b9946e269a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55065797"
---
# <a name="events-visual-basic"></a>Olaylar (Visual Basic)
Yordamları gerçekte bir sırayla yürütülen bir dizi olarak Visual Studio projesi görselleştirme ancak çoğu aktivita typu EventDriven programlarıdır — yani, yürütmenin akışını adlı dış oluşumları tarafından belirlenir *olayları*.  
  
 Bir olay uygulamanın önemli bir sorun oluştu bildiren bir sinyaldir. Örneğin, bir kullanıcı bir formdaki bir denetime tıkladığında formun yükseltebilirsiniz bir `Click` olay ve arama olayı işleyen bir yordam. Olayları da iletişim kurmak ayrı görevlere izin verin. Örneğin, uygulamanızın bir sıralama görev ayrı olarak ana uygulamadan gerçekleştireceğini varsayalım. Bir kullanıcı sıralama iptal ederse, uygulamanızı durdurmak için sıralama işlemi söyleyen bir iptal olayı gönderebilir.  
  
## <a name="event-terms-and-concepts"></a>Olay terimleri ve kavramları  
 Bu bölümde, hüküm ve Visual Basic'te olaylarla kullanılan kavramları açıklar.  
  
### <a name="declaring-events"></a>Olayları Bildirme  
 Sınıflar, yapılar, modülleri ve arabirimleri kullanarak içinde olay bildirmek `Event` anahtar sözcüğü, aşağıdaki örnekte olduğu gibi:  
  
 [!code-vb[VbVbalrEvents#24](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/events_1.vb)]  
  
### <a name="raising-events"></a>Olaylar oluşturma  
 Önemli bir sorun oluştu Duyurusu gibi bir ileti bir olaydır. İleti yayın eylemi adlı *yükseltme* olay. Visual Basic'te, olaylarla yükseltmek `RaiseEvent` deyimi, aşağıdaki örnekte olduğu gibi:  
  
 [!code-vb[VbVbalrEvents#25](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/events_2.vb)]  
  
 Burada bildirildikleri kapsamında sınıf, modül veya yapısı tetiklenen olayları gerekir. Örneğin, türetilmiş bir sınıf bir temel sınıftan devralınan olayları oluşturamaz.  
  
### <a name="event-senders"></a>Olay gönderenleri  
 Olay bildirmek özellikli herhangi bir nesne bir *olay gönderici*olarak da bilinen bir *olay kaynağı*. Formları, denetimleri ve kullanıcı tanımlı nesneler olay gönderenleri örnekleridir.  
  
### <a name="event-handlers"></a>Olay İşleyicileri  
 *Olay işleyicileri* karşılık gelen bir olay meydana geldiğinde çağrılan yordamlar. Geçerli bir alt yordam bir olay işleyicisi eşleşen bir imza ile kullanabilirsiniz. Olay kaynağı için bir değer döndüremez çünkü bir işlev ancak, bir olay işleyicisi kullanamazsınız.  
  
 Visual Basic olay gönderen, alt çizgi ve olayın adını adını birleştiren olay işleyicileri için standart bir adlandırma kuralını kullanır. Örneğin, `Click` adlı bir düğme olayı `button1` sayfadayken `Sub button1_Click`.  
  
> [!NOTE]
>  Kendi olayları için olay işleyicileri tanımlarken bu adlandırma kuralını kullanır, ancak bu zorunlu değildir öneririz; herhangi bir geçerli bir alt yordam adı kullanabilirsiniz.  
  
## <a name="associating-events-with-event-handlers"></a>Olayları olay işleyicileri ile ilişkilendirme  
 Bir olay işleyicisi kullanılabilir olmadan önce önce bu olayla kullanarak ilişkilendirmelisiniz `Handles` veya `AddHandler` deyimi.  
  
### <a name="withevents-and-the-handles-clause"></a>WithEvents ve Handles yan tümcesi  
 `WithEvents` Deyimi ve `Handles` yan tümcesi, olay işleyicileri belirtme bildirim temelli bir yöntemini sağlar. Bir nesne tarafından harekete geçirilen bir olay ile bildirilen `WithEvents` anahtar sözcüğü ile herhangi bir yordam tarafından işlenebilir bir `Handles` deyimi aşağıdaki örnekte gösterildiği gibi bu olay için:  
  
 [!code-vb[VbVbalrEvents#1](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/events_3.vb)]  
  
 `WithEvents` Deyimi ve `Handles` yan tümcesi olan genellikle en iyi seçenek olay işleyicileri kullandıkları bildirim temelli söz dizimi olay işleme kodu daha kolay hale getirdiği için okuma ve hata ayıklama için. Ancak, aşağıdaki sınırlamalar kullanımı ile ilgili dikkat edilmesi `WithEvents` değişkenleri:  
  
-   Kullanamazsınız bir `WithEvents` değişken olarak bir nesne değişkeni. Diğer bir deyişle, olarak bildiremezsiniz `Object`— değişken bildirdiğinizde, sınıf adı belirtmeniz gerekir.  
  
-   Paylaşılan olayları sınıf örneklerinin bağlı değil çünkü kullanamazsınız `WithEvents` bildirimli olarak paylaşılan olayları işlemek için. Benzer şekilde, kullanamazsınız `WithEvents` veya `Handles` olayları işlemek için bir `Structure`. Her iki durumda da kullanabileceğinizi `AddHandler` bu olayları işlemek için deyimi.  
  
-   Dizi oluşturulamıyor `WithEvents` değişkenleri.  
  
 `WithEvents` değişkenleri, bir veya daha fazla olay türünü ya da aynı türde bir olayı işlemek için bir veya daha fazla olay işleyicileri işlemek tek olay işleyicisine izin verin.  
  
 Ancak `Handles` yan tümcesi, bir olay bir olay işleyicisi ile ilişkili bir standart yoludur, olayları olay işleyicileriyle derleme zamanında ilişkilendirme ile sınırlıdır.  
  
 Bazı durumlarda, gibi form veya denetimleri ile ilişkili olayları Visual Basic otomatik olarak bir boş olay işleyicisini Saplamaları ve bir olay ile ilişkilendirir. Örneğin, bir form Tasarım modunda bir komut düğmesine çift tıkladığınızda Visual Basic boş olay işleyicisi oluşturur ve bir `WithEvents` değişken komut düğmesi için aşağıdaki kod gibi:  
  
 [!code-vb[VbVbalrEvents#26](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/events_4.vb)]  
  
### <a name="addhandler-and-removehandler"></a>AddHandler ve RemoveHandler  
 `AddHandler` Deyimi benzer `Handles` yan tümcesinde hem de bir olay işleyicisi belirtmek, izin vermek demektir. Ancak, `AddHandler`ile kullanılan `RemoveHandler`, daha büyük esneklik sağlar `Handles` dinamik olarak eklemenize olanak sağlayan yan tümcesini kaldırın ve bir olay ile ilişkili olay işleyicisini değiştirin. Paylaşılan olayları veya bir yapı olayları işlemek isterseniz kullanmalısınız `AddHandler`.  
  
 `AddHandler` iki bağımsız değişkeni alır: bir denetimin yanı sıra, bir temsilci için değerlendirilen bir ifade gibi olay gönderen bir olay adı. Temsilci sınıfı kullanarak açıkça belirtmeniz gerekmez `AddHandler`, bu yana `AddressOf` ifade her zaman temsilci bir başvuru döndürür. Aşağıdaki örnek, bir nesne tarafından harekete geçirilen bir olay bir olay işleyicisi ilişkilendirir:  
  
 [!code-vb[VbVbalrEvents#28](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/events_5.vb)]  
  
 `RemoveHandler`, aynı söz dizimini kullanır, bir olay bir olay işleyicisinden bağlantısını keser `AddHandler`. Örneğin:  
  
 [!code-vb[VbVbalrEvents#29](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/events_6.vb)]  
  
 Aşağıdaki örnekte, bir olay işleyicisi bir olay ile ilişkilendirilir ve olay tetiklenir. Olay işleyicisi, olay yakalar ve bir ileti görüntüler.  
  
 Ardından ilk olay işleyicisi kaldırılır ve farklı olay işleyicisi, olay ile ilişkilendirilir. Olayı yeniden başlatıldığında, farklı bir ileti görüntülenir.  
  
 Son olarak, ikinci olay işleyicisi kaldırılır ve bir üçüncü kez olay tetiklenir. Olay ile ilişkili bir olay işleyicisi artık yoktur çünkü hiçbir işlem yapılmaz.  
  
 [!code-vb[VbVbalrEvents#38](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/events_7.vb)]  
  
## <a name="handling-events-inherited-from-a-base-class"></a>Bir temel sınıftan devralınan olaylarını işleme  
 *Türetilmiş sınıflar*— özellikleri bir temel sınıftan devralınan sınıflar — kendi temel sınıfı kullanılarak oluşturulan olayları işleyebilir `Handles MyBase` deyimi.  
  
#### <a name="to-handle-events-from-a-base-class"></a>Bir temel sınıf olayları işlemek için  
  
-   Türetilmiş sınıf içinde olay işleyicisi ekleyerek bildirmek bir `Handles MyBase.` *eventname* deyimi, olay işleyici yordamı bildirimi satırına burada *eventname* olayda adıdır işlemekte olduğunuz temel sınıf. Örneğin:  
  
     [!code-vb[VbVbalrEvents#12](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/events_8.vb)]  
  
## <a name="related-sections"></a>İlgili Bölümler  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[İzlenecek yol: Olay bildirme ve oluşturma](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md)|Adım adım nasıl bildirme ve bir sınıf için olay açıklamasını sağlar.|  
|[İzlenecek yol: Olayları işleme](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)|Bir olay işleyici yordamı yazma işlemi gösterilmektedir.|  
|[Nasıl yapılır: Engellemekten Kaçınacak şekilde özel olayları bildirme](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)|Zaman uyumsuz olarak çağrılacak kendi olay işleyicileri izin veren özel bir olayı tanımlamak nasıl gösterir.|  
|[Nasıl yapılır: Bellekten kazanacak şekilde özel olayları bildirme](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)|Bellek olayı işlendiğinde kullanan özel bir olayı tanımlamak nasıl gösterir.|  
|[Basic'de devralınmış olay işleyicileri Visual Basic sorunlarını giderme](../../../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)|Devralınan bileşenler olay işleyicileri ile ortaya çıkan ortak sorunları listeler.|  
|[Olaylar](../../../../standard/events/index.md)|İçindeki olay modeli genel bakış sağlar [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].|  
|[Windows Forms'ta Olay İşleyicileri Oluşturma](../../../../framework/winforms/creating-event-handlers-in-windows-forms.md)|Windows Forms nesneleri ile ilişkili olayları ile nasıl çalışılacağını açıklar.|  
|[Temsilciler](../../../../visual-basic/programming-guide/language-features/delegates/index.md)|Visual Basic'te temsilciler genel bir bakış sağlar.|
