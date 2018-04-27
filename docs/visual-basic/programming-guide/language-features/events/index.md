---
title: Olaylar (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- events [Visual Basic], about events
- events [Visual Basic]
ms.assetid: 8fb0353a-e41b-4e23-b78f-da65db832f70
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c18c1ea645c9f144e2c2043af5460d6fb03f13a1
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="events-visual-basic"></a>Olaylar (Visual Basic)
Görselleştirme ancak bir [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] proje gerçekte bir sırayla yürütmek yordamları bir dizi olarak çoğu olay yönelimli programlardır — akışını anlamı adlı dış oluşumu tarafından belirlenir *olayları*.  
  
 Önemli bir şey oluştu uygulamanın bildiren bir sinyal bir olaydır. Örneğin, bir kullanıcı bir form üzerinde denetim tıkladığında formun yükseltebilirsiniz bir `Click` olay ve arama olayını işler bir yordam. Olaylar, iletişim kurmak ayrı görevleri de olanak sağlar. Örneğin, uygulamanızın sıralama görev ayrı ayrı ana uygulamadaki yaptığı söyleyin. Bir kullanıcı sıralama iptal ederse, uygulamanızın durdurmak için sıralama işlemi söyleyen bir iptal olayı gönderebilirsiniz.  
  
## <a name="event-terms-and-concepts"></a>Olay terimleri ve kavramları  
 Bu bölümde, hüküm ve Visual Basic'te olaylarla kullanılan kavramlar açıklanmaktadır.  
  
### <a name="declaring-events"></a>Olayları Bildirme  
 Sınıflar, yapılar, modüller ve arabirimleri kullanarak olayları bildirme `Event` aşağıdaki örnekteki gibi anahtar sözcüğü:  
  
 [!code-vb[VbVbalrEvents#24](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/events_1.vb)]  
  
### <a name="raising-events"></a>Olaylar oluşturma  
 Önemli oluştuğunu bildiren bir ileti gibi bir olaydır. İleti yayın eylemi adlı *oluşturma* olay. Visual Basic'te olaylarla Yükselt `RaiseEvent` aşağıdaki örnekteki gibi deyimi:  
  
 [!code-vb[VbVbalrEvents#25](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/events_2.vb)]  
  
 Olayları burada bildirilen kapsamında sınıfı, modül veya yapısı yükseltilmiş olması gerekir. Örneğin, türetilmiş bir sınıf bir taban sınıftan devralınan olayları oluşturamaz.  
  
### <a name="event-senders"></a>Olay gönderenleri  
 Bir olay oluşturma yeteneğine sahip herhangi bir nesne olan bir *olay gönderen*, olarak da bilinen bir *olay kaynağı*. Formları, denetimleri ve kullanıcı tanımlı nesneler olay gönderenleri gösterilebilir.  
  
### <a name="event-handlers"></a>Olay İşleyicileri  
 *Olay işleyicileri* karşılık gelen bir olay gerçekleştiğinde, çağrılan yordamlar. Olay işleyici eşleşen bir imza ile geçerli bir alt yordama kullanabilirsiniz. Olay kaynağı için bir değer döndüremiyor olduğundan işlevi ancak, bir olay işleyicisi kullanamazsınız.  
  
 Visual Basic standart bir adlandırma kuralının adını olay gönderen, alt çizgi ve olayın adı birleştirir olay işleyicileri için kullanır. Örneğin, `Click` adlı bir düğmeye olay `button1` sayfadayken `Sub button1_Click`.  
  
> [!NOTE]
>  Kendi olayları için olay işleyicileri tanımlarken bu adlandırma kuralını kullanın, ancak gerekli değildir öneririz; herhangi bir geçerli alt yordama adı kullanabilirsiniz.  
  
## <a name="associating-events-with-event-handlers"></a>Olayları olay işleyicileri ile ilişkilendirme  
 Olay işleyici kullanılabilir duruma gelmesi önce bir olay kullanarak ilişkilendirmelisiniz `Handles` veya `AddHandler` deyimi.  
  
### <a name="withevents-and-the-handles-clause"></a>WithEvents ve Handles tümcesi  
 `WithEvents` Deyimi ve `Handles` yan tümcesi olay işleyicileri belirtmenin bildirim temelli bir yolunu sağlar. Nesne tarafından gerçekleşen bir olay ile bildirilen `WithEvents` anahtar sözcüğü ile herhangi bir yordam tarafından işlenebilir bir `Handles` deyimi aşağıdaki örnekte gösterildiği gibi bu olay için:  
  
 [!code-vb[VbVbalrEvents#1](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/events_3.vb)]  
  
 `WithEvents` Deyimi ve `Handles` yan tümcesi olan genellikle en iyi seçenek olay işleyicileri kullandıkları Tanımlayıcı Sözdizimi olay işleme kodu kolaylaştırır çünkü okunur ve hata ayıklama. Ancak, kullanımı aşağıdaki sınırlamalar haberdar `WithEvents` değişkenleri:  
  
-   Kullanarak bir `WithEvents` değişken olarak bir nesne değişkeni. Diğer bir deyişle, olarak bildiremezsiniz `Object`— değişkeni bildirirken sınıf adı belirtmeniz gerekir.  
  
-   Sınıf örnekleri için paylaşılan olayları bağlanmayan nedeniyle kullanamazsınız `WithEvents` bildirimli olarak paylaşılan olayları işlemek için. Benzer şekilde, kullanamazsınız `WithEvents` veya `Handles` olayları işlemek için bir `Structure`. Her iki durumda da, kullandığınız `AddHandler` bu olayları işlemek için deyimi.  
  
-   Dizileri oluşturulamıyor `WithEvents` değişkenleri.  
  
 `WithEvents` değişkenleri, bir veya daha fazla türde bir olayın ya da aynı türde bir olayın işlemek için bir veya daha fazla olay işleyicileri işlemek için tek bir olay işleyicisi izin verir.  
  
 Ancak `Handles` yan tümcesi bir olayın olay işleyicisi ile ilişkilendirme standart yolu, olayları olay işleyicileri ile derleme zamanında ilişkilendirme ile sınırlıdır.  
  
 Bazı durumlarda, gibi formlar veya denetimleri ile ilişkili olaylar ile Visual Basic otomatik olarak bir boş olay işleyicisini yerleştirir ve bir olay ile ilişkilendirir. Örneğin, bir form Tasarım modunda bir komut düğmesine çift tıkladığınızda, Visual Basic boş olay işleyicisi oluşturur ve bir `WithEvents` komut düğmesi için aşağıdaki kod olduğu gibi değişken:  
  
 [!code-vb[VbVbalrEvents#26](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/events_4.vb)]  
  
### <a name="addhandler-and-removehandler"></a>AddHandler ve RemoveHandler  
 `AddHandler` Deyimi benzer `Handles` hem de bir olay işleyicisi belirtmenize olanak veren, yan tümcesinde. Ancak, `AddHandler`ile kullanılan `RemoveHandler`, daha büyük esneklik sağlar `Handles` yan tümcesi, dinamik olarak eklemenize olanak sağlayan kaldırın ve olayla ilişkili olay işleyicisini değiştirin. Paylaşılan olayları veya bir yapı olayları işlemek istiyorsanız, kullanmalısınız `AddHandler`.  
  
 `AddHandler` iki bağımsız değişkeni alır: bir denetim ve temsilciye sonucunu veren bir ifade gibi bir olay gönderenden olayın adı. Temsilci sınıfı kullanırken açıkça belirtmeniz gerekmez `AddHandler`, bu yana `AddressOf` ifadesi her zaman temsilci bir başvuru döndürür. Aşağıdaki örnekte bir nesne tarafından gerçekleşen bir olay olay işleyicisi ilişkilendirir:  
  
 [!code-vb[VbVbalrEvents#28](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/events_5.vb)]  
  
 `RemoveHandler`, aynı söz dizimini kullanır, bir olay bir olay işleyiciden bağlantısını keser `AddHandler`. Örneğin:  
  
 [!code-vb[VbVbalrEvents#29](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/events_6.vb)]  
  
 Aşağıdaki örnekte, bir olay işleyicisi bir olayla ilişkilendirilmiş ve olay tetiklenir. Olay işleyicisi olay yakalar ve bir ileti görüntüler.  
  
 Ardından ilk olay işleyicisi kaldırılır ve olayla ilişkili farklı olay işleyicisidir. Olay yeniden oluşturulduğunda farklı bir ileti görüntülenir.  
  
 Son olarak, ikinci olay işleyicisi kaldırılır ve olay üçüncü bir kez tetiklenir. Artık olduğundan olayla ilişkili olay işleyici, hiçbir işlem yapılmadı.  
  
 [!code-vb[VbVbalrEvents#38](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/events_7.vb)]  
  
## <a name="handling-events-inherited-from-a-base-class"></a>Bir taban sınıftan devralınan olayları işleme  
 *Türetilmiş sınıflar*— özelliklere bir taban sınıftan devralın sınıfları — kendi temel sınıfı kullanılarak oluşturulan olaylara işleyebilir `Handles``MyBase` deyimi.  
  
#### <a name="to-handle-events-from-a-base-class"></a>Bir temel sınıf olayları işlemek için  
  
-   Ekleyerek türetilmiş sınıfında olay işleyici bildirmek bir `Handles MyBase.` *eventname* deyimi, olay işleyici yordamı bildirimi satırına nerede *eventname* olayda adıdır işleme temel sınıf. Örneğin:  
  
     [!code-vb[VbVbalrEvents#12](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/events_8.vb)]  
  
## <a name="related-sections"></a>İlgili Bölümler  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[İzlenecek yol: Olay Bildirme ve Oluşturma](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md)|Adım adım nasıl bildirme ve bir sınıf için olaylarını açıklamasını sağlar.|  
|[İzlenecek yol: Olayları İşleme](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)|Bir olay işleyicisi yordam yazmak gösterilmiştir.|  
|[Nasıl yapılır: Engellemekten Kaçınacak Şekilde Özel Olayları Bildirme](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)|Zaman uyumsuz olarak çağrılacak kendi olay işleyicileri sağlayan özel bir olay tanımlamak gösterilmiştir.|  
|[Nasıl yapılır: Bellekten Kazanacak Şekilde Özel Olayları Bildirme](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)|Yalnızca olay işlendiğinde bellek kullanan özel bir olay tanımlamak gösterilmiştir.|  
|[Devralınmış olay işleyicileri Visual Basic sorunlarını giderme](../../../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)|Olay işleyicileri devralınan bileşenleri ile ortaya ortak sorunları listeler.|  
|[Olaylar](../../../../standard/events/index.md)|Olay modelinde genel bir bakış sağlar [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].|  
|[Windows Forms'ta Olay İşleyicileri Oluşturma](../../../../framework/winforms/creating-event-handlers-in-windows-forms.md)|Windows Forms nesnelerle ilişkilendirilen olayları ile nasıl çalışılacağını açıklar.|  
|[Temsilciler](../../../../visual-basic/programming-guide/language-features/delegates/index.md)|Visual Basic'te temsilciler genel bir bakış sağlar.|
