---
title: Olaylar Oluşturma ve İşleme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- delegate model for events
- application development [.NET], events
- application development [.NET Framework], events
- application development [.NET Core], events
- events [.NET]
- events [.NET Core]
- events [.NET Framework]
ms.assetid: b6f65241-e0ad-4590-a99f-200ce741bb1f
ms.openlocfilehash: b8ed028bc1edabf14d7b2dd67d94b28d574d2eb4
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159630"
---
# <a name="handling-and-raising-events"></a>Olayları işleme ve oluşturma

.NET 'teki olaylar, temsilci modelini temel alır. Temsilci modeli, bir abonenin ile kaydolmalarını ve sağlayıcıya bildirim almasını sağlayan [gözlemci tasarım modelini](observer-design-pattern.md)izler. Olay gönderici bir olayın gerçekleştiğini belirten bir bildirim gönderir ve olay alıcısı bu bildirimi alır ve ona bir yanıt tanımlar. Bu makalede temsilci modelinin önemli bileşenleri, uygulamalardaki olayların nasıl kullanılacağı ve kodunuzda olayların nasıl uygulanacağı açıklanmaktadır.  
  
 Windows 8. x Mağaza uygulamalarında olayları işleme hakkında daha fazla bilgi için bkz. [Olaylar ve yönlendirilmiş olaylara genel bakış](https://docs.microsoft.com/previous-versions/windows/apps/hh758286(v=win.10)).  
  
## <a name="events"></a>Olaylar

Bir olay, bir eylem oluşumuna işaret etmek için bir nesne tarafından gönderilen iletidir. Eyleme, düğme tıklamasıyla veya bir özelliğin değerini değiştirme gibi başka bir program mantığının neden olabilir. Olayı oluşturan nesneye *olay gönderici*denir. Olay gönderici, hangi nesne veya yöntemin, oluşturduğu olayları alacağını (işleyeceğimizi) bilmez. Olay, genellikle olay göndericisinin bir üyesidir; Örneğin, <xref:System.Web.UI.WebControls.Button.Click> olayı <xref:System.Web.UI.WebControls.Button> sınıfının bir üyesidir ve <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> olayı <xref:System.ComponentModel.INotifyPropertyChanged> arabirimini uygulayan sınıfın bir üyesidir.  
  
Bir olayı tanımlamak için, olay sınıfınızın imzasında C# [`event`](../../csharp/language-reference/keywords/event.md) veya Visual Basic [`Event`](../../visual-basic/language-reference/statements/event-statement.md) anahtar sözcüğünü kullanırsınız ve olay için temsilci türünü belirtirsiniz. Temsilciler sonraki bölümde açıklanmaktadır.  
  
Genellikle, bir olayı yükseltmek için, `protected` ve `virtual` (içinde C#) veya `Protected` ve `Overridable` olarak işaretlenmiş bir yöntem eklersiniz (Visual Basic). Bu yöntemi `On`*EventName*; olarak adlandırın Örneğin, `OnDataReceived`. Yöntemi, <xref:System.EventArgs> türünde bir nesne veya türetilmiş bir tür olan bir olay veri nesnesini belirten bir parametre almalıdır. Bu yöntemi, türetilmiş sınıfların olayı oluşturma mantığını geçersiz kılmasını sağlamak için sağlarsınız. Türetilmiş bir sınıf, kayıtlı temsilcilerin olayı aldığından emin olmak için her zaman temel sınıfın `On`*EventName* metodunu çağırmalıdır.  

Aşağıdaki örnek, `ThresholdReached`adlı bir olayın nasıl bildirilemeyeceğini gösterir. Olay <xref:System.EventHandler> temsilcisiyle ilişkilendirilir ve `OnThresholdReached`adlı bir yöntemde oluşturulur.  
  
 [!code-csharp[EventsOverview#1](~/samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programtruncated.cs#1)]
 [!code-vb[EventsOverview#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1truncated.vb#1)]  
  
## <a name="delegates"></a>Temsilciler

Bir temsilci, bir yönteme başvuru tutan bir türdür. Bir temsilci, başvurduğu yöntemlere yönelik dönüş türünü ve parametreleri gösteren bir imzayla ve yalnızca kendi imzasıyla eşleşen yöntemlere başvuru tutabilir. Bu nedenle bir temsilci, tür kullanımı uyumlu işlev işaretçisine veya geri aramaya eşdeğerdir. Temsilci bildirimi, bir temsilci sınıfını tanımlamak için yeterlidir.  
  
Temsilcilerin .NET 'te birçok kullanımı vardır. Olaylar bağlamında, bir temsilci olay kaynağı ve olayı işleyen kod arasında bir ara (veya işaretçi benzeri mekanizmadır). Bir temsilciyi, önceki bölümdeki örnekte gösterildiği gibi, olay bildirimine ekleyerek bir olayla ilişkilendirirsiniz. Temsilciler hakkında daha fazla bilgi için <xref:System.Delegate> sınıfına bakın.  
  
.NET, çoğu olay senaryosunu desteklemek için <xref:System.EventHandler> ve <xref:System.EventHandler%601> temsilcileri sağlar. Olay verileri içermeyen tüm olaylar için <xref:System.EventHandler> temsilcisini kullanın. Olayla ilgili verileri içeren olaylar için <xref:System.EventHandler%601> temsilcisini kullanın. Bu temsilcilerin dönüş türü değeri yoktur ve iki parametre (etkinliğin kaynağı için bir nesne ve olay verileri için bir nesne) alın.  
  
Temsilciler [çok noktaya yayın](xref:System.MulticastDelegate), yani birden çok olay işleme yöntemine başvuruları tutabilecekleri anlamına gelir. Ayrıntılar için <xref:System.Delegate> başvuru sayfasına bakın. Temsilciler, olay İşlemede esneklik ve ayrıntılı denetim sağlar. Bir temsilci, olay için kayıtlı olay işleyicilerinin bir listesini tutarak olayı oluşturan sınıf için bir olay dağıtıcısı işlevi görür.  
  
<xref:System.EventHandler> ve <xref:System.EventHandler%601> temsilcilerinin çalışmalarındaki senaryolar için bir temsilci tanımlayabilirsiniz. Bir temsilciyi tanımlamanızı gerektiren senaryolar çok nadir bir durumdur, örneğin, genel türleri tanımayan kodla çalışmanız gerekir. Bir temsilciyi C# , bildirimde [`delegate`](../../csharp/language-reference/builtin-types/reference-types.md#the-delegate-type) ve Visual Basic [`Delegate`](../../visual-basic/language-reference/statements/delegate-statement.md) anahtar sözcüğüyle işaretlersiniz. Aşağıdaki örnek, `ThresholdReachedEventHandler`adlı bir temsilcinin nasıl bildirilemeyeceğini gösterir.  
  
[!code-csharp[EventsOverview#4](~/samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programtruncated.cs#4)]
[!code-vb[EventsOverview#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1truncated.vb#4)]  
  
## <a name="event-data"></a>Olay verileri

Bir olayla ilişkili veriler bir olay veri sınıfı aracılığıyla sağlanalabilir. .NET, uygulamalarınızda kullanabileceğiniz pek çok olay veri sınıfı sağlar. Örneğin <xref:System.IO.Ports.SerialDataReceivedEventArgs> sınıfı, <xref:System.IO.Ports.SerialPort.DataReceived?displayProperty=nameWithType> olayının olay verileri sınıfıdır. .NET, tüm olay veri sınıflarının `EventArgs`ile biten bir adlandırma düzeniyle uyar. Olayın temsilcisine bakarak bir olayla hangi olay verileri sınıfının ilişkilendirildiğini belirlersiniz. Örneğin, <xref:System.IO.Ports.SerialDataReceivedEventHandler> temsilcisi, parametrelerinden biri olarak <xref:System.IO.Ports.SerialDataReceivedEventArgs> sınıfını içerir.  
  
<xref:System.EventArgs> sınıfı tüm olay veri sınıflarının temel türüdür. <xref:System.EventArgs> Ayrıca, bir olay kendisiyle ilişkilendirilmiş herhangi bir veri olmadığında kullandığınız sınıftır. Yalnızca bir şeyin meydana geldiğini ve herhangi bir veri iletmesini gerektirmeyen diğer sınıflara bildirimde bulunan bir olay oluşturduğunuzda, <xref:System.EventArgs> sınıfını temsilcideki ikinci parametre olarak ekleyin. Veri sağlanmadıysa <xref:System.EventArgs.Empty?displayProperty=nameWithType> değerini geçirebilirsiniz. <xref:System.EventHandler> temsilcisi <xref:System.EventArgs> sınıfını bir parametre olarak içerir.  
  
Özelleştirilmiş bir olay veri sınıfı oluşturmak istediğinizde, <xref:System.EventArgs>türeten bir sınıf oluşturun ve ardından olayla ilgili verileri iletmek için gereken tüm üyeleri sağlayın. Genellikle, .NET ile aynı adlandırma modelini kullanmanız ve `EventArgs`olay veri sınıfı adınızı sonlandırmalısınız.  
  
Aşağıdaki örnek, `ThresholdReachedEventArgs`adlı bir olay veri sınıfını gösterir. Bu, yükseltilen olaya özgü özellikler içerir.  
  
[!code-csharp[EventsOverview#3](~/samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programtruncated.cs#3)]
[!code-vb[EventsOverview#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1truncated.vb#3)]  
  
## <a name="event-handlers"></a>Olay işleyicileri

Bir olaya yanıt vermek için, olay alıcısında bir olay işleyicisi yöntemi tanımlarsınız. Bu yöntem, işlemekte olduğunuz olayın temsilcisinin imzasıyla aynı olmalıdır. Olay işleyicisinde, Kullanıcı bir düğmeye tıkladıktan sonra Kullanıcı girişi toplama gibi, olay ortaya çıktığında gerekli olan eylemleri gerçekleştirirsiniz. Olay gerçekleştiğinde bildirim almak için olay işleyicisi yönteminiz olaya abone olmalıdır.  
  
Aşağıdaki örnek, <xref:System.EventHandler> temsilcisinin imzasıyla eşleşen `c_ThresholdReached` adlı bir olay işleyicisi yöntemi gösterir. Yöntemi `ThresholdReached` olayına abone olur.  
  
[!code-csharp[EventsOverview#2](~/samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programtruncated.cs#2)]
[!code-vb[EventsOverview#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1truncated.vb#2)]  
  
## <a name="static-and-dynamic-event-handlers"></a>Statik ve dinamik olay işleyicileri  

.NET, abonelerin statik veya dinamik olarak olay bildirimlerine kaydolmanızı sağlar. Statik olay işleyicileri, olaylarını işleyen sınıfın tüm ömrü için geçerli olur. Dinamik olay işleyicileri, genellikle bazı koşullu program mantığına yanıt olarak program yürütmesi sırasında açıkça etkinleştirilir ve devre dışı bırakılır. Örneğin, olay bildirimleri yalnızca belirli koşullar altında gerekliyse veya bir uygulama birden çok olay işleyicisi sağlıyorsa ve çalışma zamanı koşullarını kullanmak üzere uygun olanı tanımladıysanız kullanılabilirler. Önceki bölümdeki örnek, dinamik olarak bir olay işleyicisinin nasıl ekleneceğini gösterir. Daha fazla bilgi için bkz. [Olaylar](../../visual-basic/programming-guide/language-features/events/index.md) (Visual Basic) ve [olayları](../../csharp/programming-guide/events/index.md) (içinde C#).  
  
## <a name="raising-multiple-events"></a>Birden çok olayı oluşturma  
 Sınıfınız birden çok olayı harekete geçirirse, derleyici olay temsilcisi örneği başına bir alan oluşturur. Olay sayısı büyükse, her temsilci için bir alanın depolama maliyeti kabul edilebilir olmayabilir. Bu durumlar için, .NET olay temsilcilerini depolamak üzere tercih ettiğiniz başka bir veri yapısıyla kullanabileceğiniz olay özellikleri sağlar.  
  
 Olay özellikleri olay erişimcilerine eşlik eden olay bildirimlerinden oluşur. Olay erişimcileri, depolama veri yapısından olay temsilcisi örnekleri eklemek veya kaldırmak için tanımladığınız yöntemlerdir. Olay özelliklerinin, çağrılmadan önce her olay temsilcisinin alınması gerektiğinden olay alanlarından daha yavaş olduğunu unutmayın. Denge, bellek ve hız arasındadır. Sınıfınız seyrek olarak yükseltilen çok sayıda olay tanımlıyorsa, olay özelliklerini uygulamak isteyeceksiniz. Daha fazla bilgi için bkz. [nasıl yapılır: olay özelliklerini kullanarak birden çok olayı işleme](how-to-handle-multiple-events-using-event-properties.md).  
  
## <a name="related-topics"></a>İlgili konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Nasıl yapılır: Olaylar Oluşturma ve Kullanma](how-to-raise-and-consume-events.md)|Olayları oluşturma ve kullanma örneklerini içerir.|  
|[Nasıl yapılır: Olay Özelliklerini Kullanarak Birden Çok Olayı İşleme](how-to-handle-multiple-events-using-event-properties.md)|Birden çok olayı işlemek için olay özelliklerinin nasıl kullanılacağını gösterir.|  
|[Gözlemci Tasarım Deseni](observer-design-pattern.md)|Bir abonenin bir sağlayıcıya kaydolmalarını ve bir sağlayıcıdan gelen bildirimleri almasını sağlayan tasarım modelini açıklar.|  
|[Nasıl yapılır: Bir Windows Forms Uygulamasında Olayları Kullanma](how-to-consume-events-in-a-web-forms-application.md)|Web Forms denetimi tarafından oluşturulan bir olayın nasıl işleneceğini gösterir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.EventHandler>
- <xref:System.EventHandler%601>
- <xref:System.EventArgs>
- <xref:System.Delegate>
- [Olaylar (Visual Basic)](../../visual-basic/programming-guide/language-features/events/index.md)
- [Olaylar (C# Programlama Kılavuzu)](../../csharp/programming-guide/events/index.md)
- [Olaylar ve yönlendirilmiş olaylara genel bakış (UWP uygulamaları)](/windows/uwp/xaml-platform/events-and-routed-events-overview)
