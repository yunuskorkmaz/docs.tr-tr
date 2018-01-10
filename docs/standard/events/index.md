---
title: "Olaylar Oluşturma ve İşleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- delegate model for events
- application development [.NET Framework], events
- events [.NET Framework]
ms.assetid: b6f65241-e0ad-4590-a99f-200ce741bb1f
caps.latest.revision: "23"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 49355c4271efc37a40c025c0f8275ec42e13723e
ms.sourcegitcommit: 91691981897cf8451033cb01071d8f5d94017f97
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2018
---
# <a name="handling-and-raising-events"></a>Olaylar Oluşturma ve İşleme
.NET Framework'teki olayları temsilci model üzerinde temel alır. Temsilci modeli kaydetme ve bir sağlayıcıdan bildirimleri almak abone etkinleştirir gözlemci tasarım deseni izler. Bir olay gönderen bir olay oluştu ve olay alıcı bu bildirimi alır ve bir yanıta tanımlayan bir bildirim gönderir. Bu makalede, temsilci modeli ana bileşenlerini, olayları uygulamalarında kullanma ve nasıl kodunuzda olayları uygulanacağı açıklanmaktadır.  
  
 Olay işleme hakkında bilgi edinmek için [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamaları bkz [olaylar ve yönlendirilmiş olaylara genel bakış (Windows mağazası uygulamaları)](http://go.microsoft.com/fwlink/p/?LinkId=261485).  
  
## <a name="events"></a>Olaylar  
 Bir eylem oluşumunu göstermek için bir nesne tarafından gönderilen bir iletinin bir olaydır. Eylem kullanıcı etkileşimi tarafından bir düğmeyi tıklatın veya bir özelliğin değerini değiştirmek gibi bazı diğer program mantığı tarafından gerçekleştirilen gibi neden olabilir. Olayı oluşturan nesne adında *olay gönderen*. Olay gönderen hangi nesne veya yöntemi (tanıtıcı) alacak bilmiyor yükseltir olaylar. Olay genellikle olay gönderen üyesidir; Örneğin, <xref:System.Web.UI.WebControls.Button.Click> olay üyesi olduğu <xref:System.Web.UI.WebControls.Button> sınıfı ve <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> olay uygulayan sınıf üyesi olduğu <xref:System.ComponentModel.INotifyPropertyChanged> arabirimi.  
  
 Bir olay tanımlamak için kullandığınız `event` (C# ' ta) veya `Event` (Visual Basic'te), olay imza anahtar sözcük sınıfı ve olayı için temsilci türünü belirtin. Temsilciler sonraki bölümde açıklanmaktadır.  
  
 Genellikle, bir olayı olarak işaretlenmiş bir yöntem ekleyin `protected` ve `virtual` (C# ' ta) veya `Protected` ve `Overridable` (Visual Basic'te). Bu yöntem adı `On` *EventName*; Örneğin, `OnDataReceived`. Yöntemi, bir olay veri nesnesi belirten bir parametre almalıdır. Olayı tetiklenmeden mantığı geçersiz kılmak türetilen sınıflar etkinleştirmek için bu yöntem sağlar. Türetilmiş bir sınıf her zaman çağırmalıdır `On` *EventName* yöntemi kayıtlı temsilciler olayı aldığından emin olmak için temel sınıf.  
  
 Aşağıdaki örnek, adlandırılmış bir olay bildirmek gösterilmiştir `ThresholdReached`. Olay ile ilişkilendirilmiş <xref:System.EventHandler> temsilci ve adlı bir yöntemde oluşan `OnThresholdReached`.  
  
 [!code-csharp[EventsOverview#1](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programtruncated.cs#1)]
 [!code-vb[EventsOverview#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1truncated.vb#1)]  
  
## <a name="delegates"></a>Temsilciler  
 Temsilci bir yöntem başvuru tutan bir türüdür. Bir temsilci yöntemlerinin parametrelerini ve dönüş türü başvuruyor ve imzası eşleşen yöntemleri başvuruları tutabilir gösteren bir imza ile bildirilir. Bir temsilci, böylece bir tür kullanımı uyumlu işlev işaretçisi ya da bir geri çağırma eşdeğerdir. Bir temsilci sınıf tanımlamak bir temsilci bildirimi yeterlidir.  
  
 Temsilciler .NET Framework birçok kullanımı vardır. Olayları bağlamında, bir aracı temsilcisidir (veya pointer-like mekanizması) olay kaynağı ve olayı işleyen kodu arasında. Bir temsilci sahip bir olay Olay bildiriminde temsilci türü dahil olmak üzere önceki bölümdeki örnekte gösterildiği gibi ilişkilendirebilirsiniz. Temsilciler hakkında daha fazla bilgi için bkz: <xref:System.Delegate> sınıfı.  
  
 .NET Framework sağlar <xref:System.EventHandler> ve <xref:System.EventHandler%601> çoğu olay senaryoları desteklemek için temsilciler. Kullanım <xref:System.EventHandler> olay verileri içermez tüm olaylar için temsilci. Kullanım <xref:System.EventHandler%601> olayla ilgili verileri içeren olaylar için temsilci. Bu temsilci dönüş türü değere sahip olmayan ve iki parametre (olay kaynağı için bir nesne) ve bir nesne olay verileri için gerçekleştirin.  
  
 Bunlar birden fazla olay işleme yöntemi başvuruları tutmak anlamına gelen çok noktaya yayın temsilcileri var. Ayrıntılar için bkz <xref:System.Delegate> başvuru sayfası. Temsilciler esneklik ve olay işlemede hassas bir denetim sağlar. Bir temsilci kayıtlı olay işleyicileri olayı için listesini tutarak olayını sınıf için bir olay dağıtıcı olarak görev yapar.  
  
 Senaryolar için burada <xref:System.EventHandler> ve <xref:System.EventHandler%601> temsilciler çalışmaz, bir temsilci tanımlayabilirsiniz. Genel türler tanımıyor koduyla çalışırken gerekir gibi çok nadir bir temsilci tanımlamak gerektiren senaryolar. Bir temsilci ile işaretle `delegate` (C#) ve `Delegate` (Visual Basic'te) bildirimindeki anahtar sözcüğü. Aşağıdaki örnek, adlandırılmış bir temsilci bildirmek gösterilmiştir `ThresholdReachedEventHandler`.  
  
 [!code-csharp[EventsOverview#4](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programtruncated.cs#4)]
 [!code-vb[EventsOverview#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1truncated.vb#4)]  
  
## <a name="event-data"></a>Olay Verileri  
 Olayla ilişkili verileri bir olay verileri sınıfı sağlanabilir. .NET Framework uygulamalarınızda kullanabileceğiniz birçok olay veri sınıfları sağlar. Örneğin, <xref:System.IO.Ports.SerialDataReceivedEventArgs> sınıftır olay verileri için <xref:System.IO.Ports.SerialPort.DataReceived?displayProperty=nameWithType> olay. .NET Framework tüm olay veri sınıfları ile biten bir adlandırma desenini izler `EventArgs`. Olayı için temsilci bakarak hangi olay verileri sınıfı bir olayla ilişkili belirler. Örneğin, <xref:System.IO.Ports.SerialDataReceivedEventHandler> temsilci içerir <xref:System.IO.Ports.SerialDataReceivedEventArgs> parametrelerinden biri olarak sınıf.  
  
 <xref:System.EventArgs> Sınıfı, tüm olay veri sınıfları için temel tür. <xref:System.EventArgs>Ayrıca bir olay kendisiyle ilişkilendirilmiş herhangi bir veri olmadığında kullandığınız sınıftır. Bir olay oluşturduğunuzda yalnızca yöneliktir bir şey oldu ve gerekmeyen içeriyor, herhangi bir veri geçirmek diğer sınıflar bildirmek için <xref:System.EventArgs> sınıfı temsilci de ikinci parametre olarak. Geçirebilirsiniz <xref:System.EventArgs.Empty?displayProperty=nameWithType> hiçbir veri sağlandığında değeri. <xref:System.EventHandler> Temsilci içerir <xref:System.EventArgs> sınıfı bir parametre olarak.  
  
 Özelleştirilmiş olay verileri sınıfı oluşturmak istediğinizde, türeyen bir sınıf oluşturun <xref:System.EventArgs>ve ardından olaya ilişkin veri iletmek için gerekli herhangi bir üye belirtin. Genellikle, aynı adlandırma deseni .NET Framework kullanın ve, olay verileri sınıf adı ile bitmesi gerekir `EventArgs`.  
  
 Aşağıdaki örnek, adlandırılmış bir olay verileri sınıfı gösterir `ThresholdReachedEventArgs`. Gerçekleştirilen olaya özgü özellikleri içerir.  
  
 [!code-csharp[EventsOverview#3](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programtruncated.cs#3)]
 [!code-vb[EventsOverview#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1truncated.vb#3)]  
  
## <a name="event-handlers"></a>Olay İşleyicileri  
 Bir olaya yanıt vermek için olay alıcı bir olay işleyicisi yöntemi tanımlayın. Bu yöntem, işleme olayı için temsilci imza eşleşmesi gerekir. Olay işleyicisi, olay oluşturulduğunda kullanıcı bir düğmesini tıklattıktan sonra kullanıcı girişi toplama gibi gerekli eylemleri gerçekleştirin. Olay gerçekleştiğinde bildirimleri almak için olay işleyicisi yöntemi olaya abone olmalısınız.  
  
 Adlı bir olay işleyicisi yöntemi aşağıdaki örnekte `c_ThresholdReached` imza için eşleşen <xref:System.EventHandler> temsilci. Yöntem abone `ThresholdReached` olay.  
  
 [!code-csharp[EventsOverview#2](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programtruncated.cs#2)]
 [!code-vb[EventsOverview#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1truncated.vb#2)]  
  
## <a name="static-and-dynamic-event-handlers"></a>Statik ve Dinamik Olay İşleyicileri  
 .NET Framework olay bildirimleri için statik veya dinamik olarak kaydetmek aboneleri sağlar. Statik olay işleyicileri için olayları bunlar işlemek sınıfın tüm kullanım ömrü etkindir. Dinamik olay işleyicileri açıkça etkinleştirilir ve genellikle bazı koşullu program mantığı yanıtta program yürütme sırasında devre dışı bırakıldı. Örneğin, yalnızca belirli koşullar altında olay bildirimleri gerekirse veya bir uygulama birden çok olay işleyicileri sağlar ve kullanmak için uygun bir çalışma zamanı koşullarını tanımlayın kullanılabilir. Önceki bölümdeki örnek, bir olay işleyicisi dinamik olarak eklemeyi gösterilmiştir. Daha fazla bilgi için bkz: [olayları](../../visual-basic/programming-guide/language-features/events/index.md) ve [olayları](../../csharp/programming-guide/events/index.md).  
  
## <a name="raising-multiple-events"></a>Birden Çok Olay Oluşturma  
 Sınıfınızda birden çok olay geçirirse derleyici olay temsilci örneği başına bir alanı oluşturur. Olayların sayısının büyükse, temsilci her bir alan depolama maliyetini kabul edilebilir olmayabilir. Bu durumlarda, .NET Framework olay özellikleri sağlar. olay temsilcileri depolamak için tercih ettiğiniz başka bir veri yapısı ile kullanabilirsiniz.  
  
 Olay özellikleri tarafından olay erişimcileri eşlik olay bildirimleri oluşur. Olay erişimcileri ekleyin veya depolama veri yapısından olay temsilci örneklerini kaldırmak için tanımladığınız yöntemleridir. Olay Özellikleri etkinleştirilebilir önce her olay temsilci alınmalıdır çünkü olay alanları yavaş olduğunu unutmayın. Bellek ve hız dengelemeyi olur. Sınıfınızda seyrek gerçekleştirilen birçok olay tanımlıyorsa, olay özellikleri uygulamak isteyeceksiniz. Daha fazla bilgi için bkz: [nasıl yapılır: işlemek birden çok olayları kullanarak olay özelliklerini](../../../docs/standard/events/how-to-handle-multiple-events-using-event-properties.md).  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Nasıl yapılır: Olaylar Oluşturma ve Kullanma](../../../docs/standard/events/how-to-raise-and-consume-events.md)|Oluşturma ve olayları kullanma örnekleri içerir.|  
|[Nasıl yapılır: Olay Özelliklerini Kullanarak Birden Çok Olayı İşleme](../../../docs/standard/events/how-to-handle-multiple-events-using-event-properties.md)|Olay özellikleri birden çok olayı işleme için nasıl kullanılacağını gösterir.|  
|[Gözlemci Tasarım Deseni](../../../docs/standard/events/observer-design-pattern.md)|Kaydetme ve bir sağlayıcıdan bildirimleri almak abone sağlayan tasarım deseni açıklar.|  
|[Nasıl yapılır: Bir Windows Forms Uygulamasında Olayları Kullanma](../../../docs/standard/events/how-to-consume-events-in-a-web-forms-application.md)|Web formları denetimi tarafından gerçekleştirilen bir olay nasıl ele alınacağını gösterir.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.EventHandler>  
 <xref:System.EventHandler%601>  
 <xref:System.EventArgs>  
 <xref:System.Delegate>  
 [Olaylar ve yönlendirilmiş olaylara genel bakış (UWP uygulamalar)](/windows/uwp/xaml-platform/events-and-routed-events-overview)  
 [Olaylar (Visual Basic)](../../visual-basic/programming-guide/language-features/events/index.md)  
 [Olaylar (C# programlama Kılavuzu)](../../csharp/programming-guide/events/index.md)
