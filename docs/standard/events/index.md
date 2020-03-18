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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159630"
---
# <a name="handling-and-raising-events"></a>Olayları ele alma ve büyütme

.NET'teki olaylar temsilci modelini temel alıyor. Temsilci modeli, bir abonenin bir sağlayıcıya kaydolmasını ve bildirimlerini almasını sağlayan [gözlemci tasarım desenini](observer-design-pattern.md)izler. Olay gönderen, bir olayın meydana geldiğine dair bir bildirim gönderir ve bir olay alıcısı bu bildirimi alır ve bir yanıt tanımlar. Bu makalede, temsilci modelinin ana bileşenleri, uygulamalardaki olayların nasıl tüketilmeye ne kadar açık olduğu ve kodunuzdaki olayların nasıl uygulanacağı açıklanmaktadır.  
  
 Windows 8.x Store uygulamalarındaki olayları işleme hakkında daha fazla bilgi için [Olaylar aveb'e ve yönlendirilmiş olaylara genel bakış](https://docs.microsoft.com/previous-versions/windows/apps/hh758286(v=win.10))alabiliyorum.  
  
## <a name="events"></a>Olaylar

Olay, bir eylemin oluşumunu işaret etmek için bir nesne tarafından gönderilen iletidir. Eylem, düğme tıklaması gibi kullanıcı etkileşiminden kaynaklanabilir veya bir özelliğin değerini değiştirme gibi başka bir program mantığından kaynaklanabilir. Olayı yükselten nesneye *olay gönderen*denir. Olay gönderen, hangi nesnenin veya yöntemin yükselttiği olayları alacağını (işleyeceğini) bilmiyor. Olay genellikle olay gönderenin bir üyesidir; örneğin, <xref:System.Web.UI.WebControls.Button.Click> olay <xref:System.Web.UI.WebControls.Button> sınıfın bir üyesidir ve <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> olay <xref:System.ComponentModel.INotifyPropertyChanged> arabirimi uygulayan sınıfın bir üyesidir.  
  
Bir olayı tanımlamak için, olay [`event`](../../csharp/language-reference/keywords/event.md) sınıfınızın [`Event`](../../visual-basic/language-reference/statements/event-statement.md) imzasında C# veya Visual Basic anahtar sözcük'ü kullanın ve olayın temsilci türünü belirtin. Temsilciler sonraki bölümde açıklanmıştır.  
  
Genellikle, bir olayı yükseltmek için, (C#' `protected` `virtual` da) veya `Protected` `Overridable` (Visual Basic' de) olarak işaretlenmiş bir yöntem eklersiniz. Bu yöntemi `On` *ad: EventName*; örneğin, `OnDataReceived`. Yöntem, tür <xref:System.EventArgs> veya tür türünden bir nesne olan bir olay veri nesnesi belirten bir parametre almalıdır. Türetilmiş sınıfların olayı yükseltme mantığını geçersiz kılmak için bu yöntemi sağlarsınız. Türetilen bir sınıf, `On`kayıtlı temsilcilerin olayı aldığından emin olmak için her zaman taban sınıfın *EventName* yöntemini aramalıdır.  

Aşağıdaki örnek, adı verilen bir `ThresholdReached`olayın nasıl bildirilen gösteriş olduğunu gösterir. Olay <xref:System.EventHandler> temsilci ile ilişkilidir ve adlı `OnThresholdReached`bir yöntemde yükseltilir.  
  
 [!code-csharp[EventsOverview#1](~/samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programtruncated.cs#1)]
 [!code-vb[EventsOverview#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1truncated.vb#1)]  
  
## <a name="delegates"></a>Temsilciler

Temsilci, yönteme başvuru tutan bir türdür. Bir temsilci, başvurur ğuşmetleri için iade türünü ve parametrelerini gösteren bir imzayla bildirilir ve başvuruları yalnızca imzasıyla eşleşen yöntemlere tutabilir. Bu nedenle bir temsilci, tür güvenli işlev işaretçisine veya geri çağırmaya eşdeğerdir. Temsilci bildirimi, bir temsilci sınıfını tanımlamak için yeterlidir.  
  
Temsilcilerin .NET'te birçok kullanımı vardır. Olaylar bağlamında, temsilci olay kaynağı ve olayı işleyen kod arasında bir aracı (veya işaretçi benzeri mekanizma) olduğunu. Önceki bölümde örnekte gösterildiği gibi, olay bildirimine temsilci türünü ekleyerek bir temsilciyi bir olayla ilişkilendiriniz. Temsilciler hakkında daha fazla bilgi <xref:System.Delegate> için sınıfa bakın.  
  
.NET, <xref:System.EventHandler> çoğu <xref:System.EventHandler%601> olay senaryosunu desteklemek için ve temsilcilere sağlar. Olay <xref:System.EventHandler> verilerini içermeyen tüm olaylar için temsilciyi kullanın. Olayla <xref:System.EventHandler%601> ilgili verileri içeren olaylar için temsilciyi kullanın. Bu temsilcilerin dönüş türü değeri yoktur ve iki parametre (olayın kaynağı için bir nesne ve olay verileri için bir nesne) alır.  
  
Temsilciler [çok noktaya yayındır,](xref:System.MulticastDelegate)bu da birden fazla olay işleme yöntemine başvuru tutabilecekleri anlamına gelir. Ayrıntılar için başvuru <xref:System.Delegate> sayfasına bakın. Temsilciler, olay işlemede esneklik ve ince taneli denetim sağlar. Bir temsilci, olay için kayıtlı olay işleyicilerinin listesini koruyarak olayı yükselten sınıf için bir olay göndericisi gibi davranır.  
  
<xref:System.EventHandler> Ve <xref:System.EventHandler%601> temsilcilerin çalışmadığı senaryolar için bir temsilci tanımlayabilirsiniz. Bir temsilci tanımlamanızı gerektiren senaryolar, genel leri tanımayan kodlarla çalışmanız gerektiği gibi çok nadirdir. Bildirimde C# [`delegate`](../../csharp/language-reference/builtin-types/reference-types.md#the-delegate-type) ve Visual Basic [`Delegate`](../../visual-basic/language-reference/statements/delegate-statement.md) anahtar sözcüğüyle bir temsilci işaretlersiniz. Aşağıdaki örnek, adı verilen bir `ThresholdReachedEventHandler`temsilcinin nasıl bildirilen gösteriş  
  
[!code-csharp[EventsOverview#4](~/samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programtruncated.cs#4)]
[!code-vb[EventsOverview#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1truncated.vb#4)]  
  
## <a name="event-data"></a>Olay verileri

Bir olayla ilişkili veriler bir olay veri sınıfı aracılığıyla sağlanabilir. .NET, uygulamalarınızda kullanabileceğiniz birçok olay veri sınıfı sağlar. Örneğin, <xref:System.IO.Ports.SerialDataReceivedEventArgs> sınıf <xref:System.IO.Ports.SerialPort.DataReceived?displayProperty=nameWithType> olay için olay veri sınıfıdır. .NET, tüm olay veri sınıflarını `EventArgs`. Olay için temsilciye bakarak bir olay veri sınıfıyla ilişkili olan olay veri sınıfının belirlenebiyi belirlersiniz. Örneğin, <xref:System.IO.Ports.SerialDataReceivedEventHandler> temsilci <xref:System.IO.Ports.SerialDataReceivedEventArgs> sınıfı parametrelerinden biri olarak içerir.  
  
Sınıf, <xref:System.EventArgs> tüm olay veri sınıfları için temel türüdür. <xref:System.EventArgs>ayrıca, bir olayla ilişkili herhangi bir veri yoksa kullandığınız sınıftır. Yalnızca diğer sınıflara bir şey olduğunu bildirmeyi amaçlayan ve herhangi bir veri geçişi <xref:System.EventArgs> gerekmeyen bir olay oluşturduğunuzda, sınıfı temsilcideki ikinci parametre olarak ekleyin. Veri sağlanmadığında <xref:System.EventArgs.Empty?displayProperty=nameWithType> değeri geçirebilirsiniz. Temsilci, <xref:System.EventHandler> <xref:System.EventArgs> sınıfı parametre olarak içerir.  
  
Özelleştirilmiş bir olay veri sınıfı oluşturmak istediğinizde, 'den <xref:System.EventArgs>türeyen bir sınıf oluşturun ve ardından olayla ilgili verileri aktarmak için gereken tüm üyeleri sağlayın. Genellikle, .NET ile aynı adlandırma deseni kullanmalı ve olay `EventArgs`verileri sınıf adınızı .  
  
Aşağıdaki örnekte bir olay `ThresholdReachedEventArgs`veri sınıfı adlı gösterir. Yükseltilen olaya özgü özellikler içerir.  
  
[!code-csharp[EventsOverview#3](~/samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programtruncated.cs#3)]
[!code-vb[EventsOverview#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1truncated.vb#3)]  
  
## <a name="event-handlers"></a>Olay işleyicileri

Bir olayı yanıtlamak için, olay alıcısında bir olay işleyicisi yöntemi tanımlarsınız. Bu yöntem, işlediğiniz olay için temsilcinin imzasıyla eşleşmelidir. Olay işleyicisinde, kullanıcı bir düğmeyi tıklattıktan sonra kullanıcı girişi toplamak gibi olay yükseltildiğinde gereken eylemleri gerçekleştirirsiniz. Olay gerçekleştiğinde bildirim almak için olay işleyici yönteminizin olaya abone olması gerekir.  
  
Aşağıdaki örnek, temsilcinin imzasıyla `c_ThresholdReached` eşleşen adlandırılmış <xref:System.EventHandler> bir olay işleyicisi yöntemini gösterir. Yöntem `ThresholdReached` olaya abone dir.  
  
[!code-csharp[EventsOverview#2](~/samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programtruncated.cs#2)]
[!code-vb[EventsOverview#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1truncated.vb#2)]  
  
## <a name="static-and-dynamic-event-handlers"></a>Statik ve dinamik olay işleyicileri  

.NET, abonelerin olay bildirimleri için statik veya dinamik olarak kaydolmasını sağlar. Statik olay işleyicileri, olayları işlettikleri sınıfın tüm yaşamı boyunca etkindir. Dinamik olay işleyicileri, genellikle bazı koşullu program mantığına yanıt olarak program yürütme sırasında açıkça etkinleştirilir ve devre dışı bırakılır. Örneğin, olay bildirimleri yalnızca belirli koşullar altında gerekliyse veya bir uygulama birden çok olay işleyicisi sağlarsa ve çalışma zamanı koşulları kullanılacak uygun olanı tanımlıyorsa kullanılabilir. Önceki bölümdeki örnek, bir olay işleyicisinin dinamik olarak nasıl ekleyeceğini gösterir. Daha fazla bilgi için [Olaylar](../../visual-basic/programming-guide/language-features/events/index.md) (Visual Basic) ve [Olaylar](../../csharp/programming-guide/events/index.md) (C#'da) bakın.  
  
## <a name="raising-multiple-events"></a>Birden çok olayı yükseltme  
 Sınıfınız birden çok olay yükseltiyorsa, derleyici olay temsilcisi örneği başına bir alan oluşturur. Olay sayısı büyükse, temsilci başına bir alanın depolama maliyeti kabul edilemez. Bu durumlar için .NET, olay temsilcilerini depolamak için seçtiğiniz başka bir veri yapısıyla kullanabileceğiniz olay özellikleri sağlar.  
  
 Olay özellikleri, olay erişime girenlerin eşlik ettiği olay bildirimlerinden oluşur. Olay erişime girenler, olay temsilcisi örneklerini depolama veri yapısından eklemek veya kaldırmak için tanımladığınız yöntemlerdir. Her olay temsilcisi nin çağrılmadan önce alınması gerektiğinden, olay özelliklerinin olay alanlarından daha yavaş olduğunu unutmayın. Denge hafıza ve hız arasındadır. Sınıfınız seyrek olarak yükseltilmiş birçok olay tanımlıyorsa, olay özelliklerini uygulamak isteyeceksiniz. Daha fazla bilgi için [bkz: Olay Özelliklerini Kullanarak Birden Çok Olayı İşletmek.](how-to-handle-multiple-events-using-event-properties.md)  
  
## <a name="related-topics"></a>İlgili konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Nasıl yapılır: Olaylar Oluşturma ve Kullanma](how-to-raise-and-consume-events.md)|Yetiştirme ve tüketen olaylara örnekler içerir.|  
|[Nasıl yapılır: Olay Özelliklerini Kullanarak Birden Çok Olayı İşleme](how-to-handle-multiple-events-using-event-properties.md)|Birden çok olayı işlemek için olay özelliklerinin nasıl kullanılacağını gösterir.|  
|[Gözlemci Tasarım Deseni](observer-design-pattern.md)|Bir abonenin bir sağlayıcıya kaydolmasını ve bildirimlerini almasını sağlayan tasarım deseni açıklar.|  
|[Nasıl yapılır: Bir Windows Formları Uygulamasında Olayları Kullanma](how-to-consume-events-in-a-web-forms-application.md)|Web Forms denetimi tarafından yükseltilen bir olayın nasıl işleyeceğini gösterir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.EventHandler>
- <xref:System.EventHandler%601>
- <xref:System.EventArgs>
- <xref:System.Delegate>
- [Olaylar (Visual Basic)](../../visual-basic/programming-guide/language-features/events/index.md)
- [Olaylar (C# Programlama Kılavuzu)](../../csharp/programming-guide/events/index.md)
- [Olaylar ve yönlendirilmiş olaylara genel bakış (UWP uygulamaları)](/windows/uwp/xaml-platform/events-and-routed-events-overview)
