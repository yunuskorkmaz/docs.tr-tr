---
title: Olaylar Oluşturma ve İşleme
description: Temsilci modelini temel alan .NET olaylarını işleme ve oluşturmayı öğrenin. Bu model, aboneler tarafından kayıt yaptırmasına veya sağlayıcılardan bildirimler almasına olanak tanır.
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
ms.openlocfilehash: 83799b0f4c6d6503825ce271fed4bffa7a9775b9
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90545709"
---
# <a name="handling-and-raising-events"></a>Olayları işleme ve oluşturma

.NET 'teki olaylar, temsilci modelini temel alır. Temsilci modeli, bir abonenin ile kaydolmalarını ve sağlayıcıya bildirim almasını sağlayan [gözlemci tasarım modelini](observer-design-pattern.md)izler. Olay gönderici bir olayın gerçekleştiğini belirten bir bildirim gönderir ve olay alıcısı bu bildirimi alır ve ona bir yanıt tanımlar. Bu makalede temsilci modelinin önemli bileşenleri, uygulamalardaki olayların nasıl kullanılacağı ve kodunuzda olayların nasıl uygulanacağı açıklanmaktadır.  
  
 Windows 8. x Mağaza uygulamalarında olayları işleme hakkında daha fazla bilgi için bkz. [Olaylar ve yönlendirilmiş olaylara genel bakış](/previous-versions/windows/apps/hh758286(v=win.10)).  
  
## <a name="events"></a>Ekinlikler

Bir olay, bir eylem oluşumuna işaret etmek için bir nesne tarafından gönderilen iletidir. Eyleme, düğme tıklamasıyla veya bir özelliğin değerini değiştirme gibi başka bir program mantığının neden olabilir. Olayı oluşturan nesneye *olay gönderici*denir. Olay gönderici, hangi nesne veya yöntemin, oluşturduğu olayları alacağını (işleyeceğimizi) bilmez. Olay, genellikle olay göndericisinin bir üyesidir; Örneğin, <xref:System.Web.UI.WebControls.Button.Click> olayı sınıfının bir üyesidir <xref:System.Web.UI.WebControls.Button> ve <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> olay, arabirimi uygulayan sınıfın bir üyesidir <xref:System.ComponentModel.INotifyPropertyChanged> .  
  
Bir olayı tanımlamak için, [`event`](../../csharp/language-reference/keywords/event.md) [`Event`](../../visual-basic/language-reference/statements/event-statement.md) Event sınıfınızın imzasında C# veya Visual Basic anahtar sözcüğünü kullanırsınız ve olay için temsilci türünü belirtirsiniz. Temsilciler sonraki bölümde açıklanmaktadır.  
  
Genellikle, bir olayı yükseltmek için `protected` ve `virtual` (C# ' de) veya `Protected` ve `Overridable` (Visual Basic) olarak işaretlenmiş bir yöntem eklersiniz. Bu yöntemin bulunduğu adı `On` *EventName*; Örneğin, `OnDataReceived` . Yöntemi, türünde bir nesne veya türetilmiş bir tür olan bir olay veri nesnesini belirten bir parametre almalıdır <xref:System.EventArgs> . Bu yöntemi, türetilmiş sınıfların olayı oluşturma mantığını geçersiz kılmasını sağlamak için sağlarsınız. Türetilmiş bir sınıf, `On` kayıtlı temsilcilerin olayı aldığından emin olmak için her zaman temel sınıfın *EventName* metodunu çağırmalıdır.  

Aşağıdaki örnek adlı bir olayın nasıl bildirilemeyeceğini gösterir `ThresholdReached` . Olay <xref:System.EventHandler> temsilciyle ilişkilendirilir ve adlı bir yöntemde oluşturulur `OnThresholdReached` .  
  
 [!code-csharp[EventsOverview#1](~/samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programtruncated.cs#1)]
 [!code-vb[EventsOverview#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1truncated.vb#1)]  
  
## <a name="delegates"></a>Temsilciler

Bir temsilci, bir yönteme başvuru tutan bir türdür. Bir temsilci, başvurduğu yöntemlere yönelik dönüş türünü ve parametreleri gösteren bir imzayla ve yalnızca kendi imzasıyla eşleşen yöntemlere başvuru tutabilir. Bu nedenle bir temsilci, tür kullanımı uyumlu işlev işaretçisine veya geri aramaya eşdeğerdir. Temsilci bildirimi, bir temsilci sınıfını tanımlamak için yeterlidir.  
  
Temsilcilerin .NET 'te birçok kullanımı vardır. Olaylar bağlamında, bir temsilci olay kaynağı ve olayı işleyen kod arasında bir ara (veya işaretçi benzeri mekanizmadır). Bir temsilciyi, önceki bölümdeki örnekte gösterildiği gibi, olay bildirimine ekleyerek bir olayla ilişkilendirirsiniz. Temsilciler hakkında daha fazla bilgi için, <xref:System.Delegate> sınıfına bakın.  
  
.NET, <xref:System.EventHandler> <xref:System.EventHandler%601> çoğu olay senaryosunu desteklemek için ve temsilcileri sağlar. <xref:System.EventHandler>Olay verileri içermeyen tüm olaylar için temsilciyi kullanın. <xref:System.EventHandler%601>Olayla ilgili verileri içeren olaylar için temsilciyi kullanın. Bu temsilcilerin dönüş türü değeri yoktur ve iki parametre (etkinliğin kaynağı için bir nesne ve olay verileri için bir nesne) alın.  
  
Temsilciler [çok noktaya yayın](xref:System.MulticastDelegate), yani birden çok olay işleme yöntemine başvuruları tutabilecekleri anlamına gelir. Ayrıntılar için <xref:System.Delegate> başvuru sayfasına bakın. Temsilciler, olay İşlemede esneklik ve ayrıntılı denetim sağlar. Bir temsilci, olay için kayıtlı olay işleyicilerinin bir listesini tutarak olayı oluşturan sınıf için bir olay dağıtıcısı işlevi görür.  
  
<xref:System.EventHandler>Ve <xref:System.EventHandler%601> temsilcilerin çalışmalarındaki senaryolarda bir temsilci tanımlayabilirsiniz. Bir temsilciyi tanımlamanızı gerektiren senaryolar çok nadir bir durumdur, örneğin, genel türleri tanımayan kodla çalışmanız gerekir. Bir temsilciyi, [`delegate`](../../csharp/language-reference/builtin-types/reference-types.md#the-delegate-type) bildiriminde C# ve Visual Basic [`Delegate`](../../visual-basic/language-reference/statements/delegate-statement.md) anahtar sözcüğüyle işaretlemelisiniz. Aşağıdaki örnek adında bir temsilcinin nasıl bildirilemeyeceğini gösterir `ThresholdReachedEventHandler` .  
  
[!code-csharp[EventsOverview#4](~/samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programtruncated.cs#4)]
[!code-vb[EventsOverview#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1truncated.vb#4)]  
  
## <a name="event-data"></a>Olay verileri

Bir olayla ilişkili veriler bir olay veri sınıfı aracılığıyla sağlanalabilir. .NET, uygulamalarınızda kullanabileceğiniz pek çok olay veri sınıfı sağlar. Örneğin, sınıfı, <xref:System.IO.Ports.SerialDataReceivedEventArgs> olay için olay veri sınıfıdır <xref:System.IO.Ports.SerialPort.DataReceived?displayProperty=nameWithType> . .NET, tüm olay veri sınıflarının ile sonundaki bir adlandırma düzeniyle uyar `EventArgs` . Olayın temsilcisine bakarak bir olayla hangi olay verileri sınıfının ilişkilendirildiğini belirlersiniz. Örneğin, <xref:System.IO.Ports.SerialDataReceivedEventHandler> temsilci <xref:System.IO.Ports.SerialDataReceivedEventArgs> sınıfını parametrelerinden biri olarak içerir.  
  
<xref:System.EventArgs>Sınıfı, tüm olay veri sınıflarının temel türüdür. <xref:System.EventArgs> Ayrıca, bir olay kendisiyle ilişkilendirilmiş herhangi bir veri içermiyorsa kullandığınız sınıftır. Yalnızca bir şeyin meydana geldiğini ve herhangi bir veri geçmesini gerektirmeyen diğer sınıflara bildirimde bulunan bir olay oluşturduğunuzda, <xref:System.EventArgs> temsilciyi temsilciye ikinci parametre olarak ekleyin. <xref:System.EventArgs.Empty?displayProperty=nameWithType>Veri sağlanmadıysa değeri geçirebilirsiniz. <xref:System.EventHandler>Temsilci, <xref:System.EventArgs> sınıfını bir parametre olarak içerir.  
  
Özelleştirilmiş bir olay veri sınıfı oluşturmak istediğinizde, öğesinden türetilen bir sınıf oluşturun <xref:System.EventArgs> ve ardından olayla ilgili verileri geçirmek için gereken tüm üyeleri sağlayın. Genellikle, .NET ile aynı adlandırma modelini kullanmanız ve olay veri sınıfı adınızı ile sonlandırmalısınız `EventArgs` .  
  
Aşağıdaki örnek adlı bir olay veri sınıfını gösterir `ThresholdReachedEventArgs` . Bu, yükseltilen olaya özgü özellikler içerir.  
  
[!code-csharp[EventsOverview#3](~/samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programtruncated.cs#3)]
[!code-vb[EventsOverview#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1truncated.vb#3)]  
  
## <a name="event-handlers"></a>Olay işleyicileri

Bir olaya yanıt vermek için, olay alıcısında bir olay işleyicisi yöntemi tanımlarsınız. Bu yöntem, işlemekte olduğunuz olayın temsilcisinin imzasıyla aynı olmalıdır. Olay işleyicisinde, Kullanıcı bir düğmeye tıkladıktan sonra Kullanıcı girişi toplama gibi, olay ortaya çıktığında gerekli olan eylemleri gerçekleştirirsiniz. Olay gerçekleştiğinde bildirim almak için olay işleyicisi yönteminiz olaya abone olmalıdır.  
  
Aşağıdaki örnek, `c_ThresholdReached` temsilci için imzayla eşleşen adlı bir olay işleyicisi yöntemini gösterir <xref:System.EventHandler> . Yöntemi olaya abone olur `ThresholdReached` .  
  
[!code-csharp[EventsOverview#2](~/samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programtruncated.cs#2)]
[!code-vb[EventsOverview#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1truncated.vb#2)]  
  
## <a name="static-and-dynamic-event-handlers"></a>Statik ve dinamik olay işleyicileri  

.NET, abonelerin statik veya dinamik olarak olay bildirimlerine kaydolmanızı sağlar. Statik olay işleyicileri, olaylarını işleyen sınıfın tüm ömrü için geçerli olur. Dinamik olay işleyicileri, genellikle bazı koşullu program mantığına yanıt olarak program yürütmesi sırasında açıkça etkinleştirilir ve devre dışı bırakılır. Örneğin, olay bildirimleri yalnızca belirli koşullar altında gerekliyse veya bir uygulama birden çok olay işleyicisi sağlıyorsa ve çalışma zamanı koşullarını kullanmak üzere uygun olanı tanımladıysanız kullanılabilirler. Önceki bölümdeki örnek, dinamik olarak bir olay işleyicisinin nasıl ekleneceğini gösterir. Daha fazla bilgi için bkz. [Olaylar](../../visual-basic/programming-guide/language-features/events/index.md) (Visual Basic) ve [olayları](../../csharp/programming-guide/events/index.md) (C# ' ta).  
  
## <a name="raising-multiple-events"></a>Birden çok olayı oluşturma  
 Sınıfınız birden çok olayı harekete geçirirse, derleyici olay temsilcisi örneği başına bir alan oluşturur. Olay sayısı büyükse, her temsilci için bir alanın depolama maliyeti kabul edilebilir olmayabilir. Bu durumlar için, .NET olay temsilcilerini depolamak üzere tercih ettiğiniz başka bir veri yapısıyla kullanabileceğiniz olay özellikleri sağlar.  
  
 Olay özellikleri olay erişimcilerine eşlik eden olay bildirimlerinden oluşur. Olay erişimcileri, depolama veri yapısından olay temsilcisi örnekleri eklemek veya kaldırmak için tanımladığınız yöntemlerdir. Olay özelliklerinin, çağrılmadan önce her olay temsilcisinin alınması gerektiğinden olay alanlarından daha yavaş olduğunu unutmayın. Denge, bellek ve hız arasındadır. Sınıfınız seyrek olarak yükseltilen çok sayıda olay tanımlıyorsa, olay özelliklerini uygulamak isteyeceksiniz. Daha fazla bilgi için bkz. [nasıl yapılır: olay özelliklerini kullanarak birden çok olayı işleme](how-to-handle-multiple-events-using-event-properties.md).  
  
## <a name="related-topics"></a>İlgili konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Nasıl yapılır: Olaylar Oluşturma ve Kullanma](how-to-raise-and-consume-events.md)|Olayları oluşturma ve kullanma örneklerini içerir.|  
|[Nasıl yapılır: Olay Özelliklerini Kullanarak Birden Çok Olayı İşleme](how-to-handle-multiple-events-using-event-properties.md)|Birden çok olayı işlemek için olay özelliklerinin nasıl kullanılacağını gösterir.|  
|[Gözlemci tasarım kalıbı](observer-design-pattern.md)|Bir abonenin bir sağlayıcıya kaydolmalarını ve bir sağlayıcıdan gelen bildirimleri almasını sağlayan tasarım modelini açıklar.|  
|[Nasıl yapılır: Bir Windows Formları Uygulamasında Olayları Kullanma](how-to-consume-events-in-a-web-forms-application.md)|Web Forms denetimi tarafından oluşturulan bir olayın nasıl işleneceğini gösterir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.EventHandler>
- <xref:System.EventHandler%601>
- <xref:System.EventArgs>
- <xref:System.Delegate>
- [Olaylar (Visual Basic)](../../visual-basic/programming-guide/language-features/events/index.md)
- [Olaylar (C# Programlama Kılavuzu)](../../csharp/programming-guide/events/index.md)
- [Olaylar ve yönlendirilmiş olaylara genel bakış (UWP uygulamaları)](/windows/uwp/xaml-platform/events-and-routed-events-overview)
