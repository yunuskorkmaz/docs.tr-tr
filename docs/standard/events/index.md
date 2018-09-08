---
title: Olaylar Oluşturma ve İşleme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- delegate model for events
- application development [.NET Framework], events
- events [.NET Framework]
ms.assetid: b6f65241-e0ad-4590-a99f-200ce741bb1f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f5d106dd3b7b9a7a0aeedca86e63a6fccbb1cc27
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44192491"
---
# <a name="handling-and-raising-events"></a>Olaylar Oluşturma ve İşleme
.NET Framework olayları temsilci modeline dayanır. Temsilci modeli kaydedin ve bir sağlayıcıdan bildirimleri almak abone sağlayan gözlemci tasarım deseni izler. Olay gönderen olayın olduğuna ve olay alıcısı bu bildirimi alır ve bir yanıt tanımlar bir bildirim iter. Bu makalede temsilci modelinin ana bileşenleri, uygulamalarda olayların kullanma ve kodunuzda olayların nasıl açıklar.  
  
 Windows 8.x Store uygulamalarında olayları işleme hakkında daha fazla bilgi için bkz: [olaylar ve yönlendirilmiş olaylara genel bakış](https://docs.microsoft.com/previous-versions/windows/apps/hh758286(v=win.10)).  
  
## <a name="events"></a>Olaylar  
 Bir olay bir eylemin oluşumunu bildirmek için nesne tarafından gönderilen bir iletidir. Eylemi, bir düğmeye tıklayın veya bir özelliğin değerinin değiştirilmesi gibi bazı başka bir programın mantığı tarafından gerçekleştirilen gibi kullanıcı etkileşimi tarafından kaynaklanabilir. Olayı başlatan nesne adında *olay gönderici*. Olay gönderici hangi nesnenin veya yöntemin alacağını (işleyeceğini) bilmez bilmemektedir olayları. Olay genellikle olay gönderici üyesidir; Örneğin, <xref:System.Web.UI.WebControls.Button.Click> olay üyesi olduğu <xref:System.Web.UI.WebControls.Button> sınıfı ve <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> olay uygulayan sınıfın bir üyesidir <xref:System.ComponentModel.INotifyPropertyChanged> arabirimi.  
  
 Bir olayı tanımlamak için kullandığınız `event` (C# ' de) veya `Event` (Visual Basic'te) anahtar sözcüğü, olay imzasında sınıfı ve olay için temsilci türünü belirtin. Temsilciler sonraki bölümde açıklanmaktadır.  
  
 Genellikle, bir olayı yükseltmek için olarak işaretlenmiş bir yöntemi eklemeniz `protected` ve `virtual` (C# ' de) veya `Protected` ve `Overridable` (Visual Basic'te). Bu yöntem adı `On` *EventName*; Örneğin, `OnDataReceived`. Yöntemi, bir olay veri nesnesini belirleyen bir parametre almalıdır. Bu yöntem, türetilen sınıfların, olayı mantığını geçersiz kılmasını etkinleştirmek için sağladığınız. Türetilmiş bir sınıf her zaman çağırmalıdır `On` *EventName* yöntemi kayıtlı temsilcilerin olayı aldıklarından emin olmak için temel sınıf.  
  
 Aşağıdaki örnek adlı bir olayın nasıl belirtileceğini gösterir `ThresholdReached`. Olay ile ilişkili <xref:System.EventHandler> adlı bir yöntemde oluşturulur ve temsilci `OnThresholdReached`.  
  
 [!code-csharp[EventsOverview#1](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programtruncated.cs#1)]
 [!code-vb[EventsOverview#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1truncated.vb#1)]  
  
## <a name="delegates"></a>Temsilciler  
 Bir temsilci bir yönteme başvuru tutan bir türdür. Bir temsilci başvuruyor ve yalnızca imzasıyla eşleşen yöntemlere olan başvuruları tutabilen yöntemleri için parametre ve dönüş türünü gösteren bir imzayla bildirilir. Bir temsilci, bu nedenle bir tür kullanımı uyumlu işlev işaretçisi veya bir geri çağırma eşdeğerdir. Temsilci bildirimi temsilci sınıfını tanımlamakta yeterlidir.  
  
 Temsilciler .NET Framework'te pek çok kullanımı sahiptir. Olayların bağlamında, bir aracı bir metot temsilcisi mi (veya işaretçi benzeri mekanizma) olay kaynağı ve olayı işleyen kod arasında. Bir temsilci ile bir olay temsilci türü olay bildirimine dahil ederek önceki bölümdeki örnekte gösterildiği gibi ilişkilendirebilirsiniz. Temsilciler hakkında daha fazla bilgi için bkz. <xref:System.Delegate> sınıfı.  
  
 .NET Framework sağlar <xref:System.EventHandler> ve <xref:System.EventHandler%601> çok olay senaryosunu desteklemek için temsilciler. Kullanım <xref:System.EventHandler> olay verilerini içermeyen tüm olaylar için temsilci. Kullanım <xref:System.EventHandler%601> olay hakkında veri içeren olaylar için temsilci. Bu temsilciler hiçbir dönüş türü değeri yoktur ve iki parametre (olay kaynağı için bir nesne) ve olay verileri için bir nesne alır.  
  
 Birden fazla olay işleme yöntemine yapılan başvuruları tutabilen anlamına gelen çok noktaya yayın temsilcileri, bir. Ayrıntılar için bkz <xref:System.Delegate> başvuru sayfası. Temsilciler, esneklik ve olay işlemede ayrıntılı denetim sağlar. Bir temsilci, olay kayıtlı olay işleyicilerinin bir listesini tutarak olayı yükselten sınıf için olay dağıtıcısı rolü olarak görev yapar.  
  
 Senaryolar için burada <xref:System.EventHandler> ve <xref:System.EventHandler%601> temsilcilerinin çalışmadığı, bir temsilci tanımlayabilirsiniz. Bir temsilci tanımlama gerektiren senaryolar ne zaman, genel türleri tanımayan kodla çalışmanız gerekmesi gibi nadir rastlanır. Bir temsilci ile işaretle `delegate` (C#) ve `Delegate` (Visual Basic'te) bildirimindeki anahtar sözcüğü. Aşağıdaki örnek adlı bir temsilcinin nasıl belirtileceğini gösterir `ThresholdReachedEventHandler`.  
  
 [!code-csharp[EventsOverview#4](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programtruncated.cs#4)]
 [!code-vb[EventsOverview#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1truncated.vb#4)]  
  
## <a name="event-data"></a>Olay Verileri  
 Bir olay ile ilişkilendirilen veri bir olay verisi sınıfı üzerinden sağlanabilir. .NET Framework, uygulamalarınızda kullanabileceğiniz birçok olay veri sınıfı sağlar. Örneğin, <xref:System.IO.Ports.SerialDataReceivedEventArgs> için olay veri sınıfı <xref:System.IO.Ports.SerialPort.DataReceived?displayProperty=nameWithType> olay. .NET Framework, tüm olay veri sınıfları ile biten bir adlandırma desenini izler `EventArgs`. Siz hangi olay veri sınıfı bir olay ile ilişkilendirilmiş olan olay için temsilciye bakarak belirlersiniz. Örneğin, <xref:System.IO.Ports.SerialDataReceivedEventHandler> temsilci içeren <xref:System.IO.Ports.SerialDataReceivedEventArgs> parametrelerinden biri olarak sınıf.  
  
 <xref:System.EventArgs> Sınıfı, tüm olay veri sınıfları için temel tür. <xref:System.EventArgs> Ayrıca bir olay ile ilişkili herhangi bir veri olmadığında kullandığınız sınıftır. Bir olay oluşturduğunuzda yalnızca yöneliktir, bir sorun oldu ve gerekmeyen herhangi bir veri diğer sınıflara <xref:System.EventArgs> temsilci ikinci parametre olarak sınıf. Geçirebilirsiniz <xref:System.EventArgs.Empty?displayProperty=nameWithType> hiçbir veri sağlanmadığında değeri. <xref:System.EventHandler> Temsilci içeren <xref:System.EventArgs> bir parametre olarak sınıf.  
  
 Özelleştirilmiş olay veri sınıfı oluşturmak istediğinizde, türetilen bir sınıf oluşturmanız <xref:System.EventArgs>ve ardından ve olayla ilişkili verileri aktarmak için gerekli herhangi bir üyeyi sağlayın. Genellikle, .NET Framework aynı adlandırma düzeni kullanın ve olay veri sınıfı adınızı ile bitmesi gerekir `EventArgs`.  
  
 Aşağıdaki örnekte adlı bir olay veri sınıfı göstermektedir `ThresholdReachedEventArgs`. Bu, gerçekleştirilen olaya özgü özellikleri içerir.  
  
 [!code-csharp[EventsOverview#3](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programtruncated.cs#3)]
 [!code-vb[EventsOverview#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1truncated.vb#3)]  
  
## <a name="event-handlers"></a>Olay İşleyicileri  
 Bir olaya yanıt vermek için olay alıcısında bir olay işleyici yöntemi tanımlayın. Bu yöntem, işlemekte olduğunuz olay için temsilcisinin imzasıyla eşleşmelidir. Olay işleyicisi, olay oluşturulduğunda, kullanıcı bir düğmeyi tıklattıktan sonra kullanıcı girişinin toplanması gibi gerekli eylemleri gerçekleştirin. Olay ortaya çıktığında bildirimleri almak için olay işleyicisi yönteminiz olaya abone olmalıdır.  
  
 Aşağıdaki örnekte adlı bir olay işleyicisi yöntemini göstermektedir `c_ThresholdReached` imzasıyla eşleşen <xref:System.EventHandler> temsilci. Yöntem abone `ThresholdReached` olay.  
  
 [!code-csharp[EventsOverview#2](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programtruncated.cs#2)]
 [!code-vb[EventsOverview#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1truncated.vb#2)]  
  
## <a name="static-and-dynamic-event-handlers"></a>Statik ve Dinamik Olay İşleyicileri  
 .NET Framework, abonelerin statik veya dinamik olarak olay bildirimlerine kaydetmek sağlar. Statik olay işleyiciler, olaylarını işledikleri sınıfın ömrü için geçerli olur. Dinamik olay işleyicileri açıkça etkinleştirilir ve program yürütme sırasında genellikle bazı koşullu program mantığı yanıtta devre dışı bırakıldı. Örneğin, olay bildirimleri yalnızca belirli koşullar altında gerekirse ya da uygulama çoklu olay işleyicileri sağlıyorsa ve uygun birini kullanmak için çalışma zamanı koşullarını tanımlayın kullanılabilir. Önceki bölümdeki örnek, dinamik olarak bir olay işleyicisi eklemek gösterilmektedir. Daha fazla bilgi için [olayları](../../visual-basic/programming-guide/language-features/events/index.md) ve [olayları](../../csharp/programming-guide/events/index.md).  
  
## <a name="raising-multiple-events"></a>Birden Çok Olay Oluşturma  
 Sınıfınız birden çok olayı harekete geçirirse derleyici olay temsilci örneği başına tek alan oluşturur. Olay sayısı büyükse, her temsilci tek bir alanın depolama maliyeti kabul edilebilir olmayabilir. Bu durumlarda, .NET Framework olay özelliklerini sağlar. olay temsilcilerini depolamak için seçtiğiniz başka bir veri yapısı ile kullanabilirsiniz.  
  
 Olay özellikleri, olay erişimcileri ile birlikte olay bildirimlerinden oluşur. Olay erişimcileri eklemek veya olay temsilci örneklerini depolama veri yapısından kaldırmak için tanımladığınız yöntemlerdir. Her olay temsilcisinin çağrılmadan önce alınması gerektiğinden olay özelliklerinin olay alanlarından yavaş olduğunu unutmayın. Denge, bellek ve hız arasında olur. Sınıfınız seyrek oluşan birçok olay tanımlıyorsa olay özelliklerini uygulamak isteyeceksiniz. Daha fazla bilgi için [nasıl yapılır: işleme birden çok olayları kullanarak olay özelliklerini](../../../docs/standard/events/how-to-handle-multiple-events-using-event-properties.md).  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Nasıl yapılır: Olaylar Oluşturma ve Kullanma](../../../docs/standard/events/how-to-raise-and-consume-events.md)|Olayları oluşturma ve tüketme örnekleri içerir.|  
|[Nasıl yapılır: Olay Özelliklerini Kullanarak Birden Çok Olayı İşleme](../../../docs/standard/events/how-to-handle-multiple-events-using-event-properties.md)|Olay özellikleri birden çok olayı işlemek için nasıl kullanılacağını gösterir.|  
|[Gözlemci Tasarım Deseni](../../../docs/standard/events/observer-design-pattern.md)|Kaydolun ve bir sağlayıcıdan bildirimleri almak abone sağlayan tasarım düzenini açıklar.|  
|[Nasıl yapılır: Bir Windows Forms Uygulamasında Olayları Kullanma](../../../docs/standard/events/how-to-consume-events-in-a-web-forms-application.md)|Web Forms denetimi tarafından oluşturulan bir olayın nasıl işleneceğini gösterir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.EventHandler>  
- <xref:System.EventHandler%601>  
- <xref:System.EventArgs>  
- <xref:System.Delegate>  
- [Olaylar ve yönlendirilmiş olaylara genel bakış (UWP uygulamaları)](/windows/uwp/xaml-platform/events-and-routed-events-overview)  
- [Olaylar (Visual Basic)](../../visual-basic/programming-guide/language-features/events/index.md)  
- [Olaylar (C# programlama Kılavuzu)](../../csharp/programming-guide/events/index.md)
