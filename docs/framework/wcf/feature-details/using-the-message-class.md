---
title: "İleti Sınıfını Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: d1d62bfb-2aa3-4170-b6f8-c93d3afdbbed
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5c3e33f4db403fdc4ad1d4efd14282fe2beac8dc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="using-the-message-class"></a>İleti Sınıfını Kullanma
<xref:System.ServiceModel.Channels.Message> Sınıfı için temel [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]. İstemciler ve hizmetler arasındaki tüm iletişimi sonuçta sonuçlanır <xref:System.ServiceModel.Channels.Message> örnekleri gönderilen ve alınan.  
  
 Genellikle ile etkileşime geçmez <xref:System.ServiceModel.Channels.Message> doğrudan sınıfı. Bunun yerine, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet modeli oluşturur, gibi verileri sözleşmeleri, ileti sözleşmeleri ve işlemi sözleşmeleri gelen ve giden iletiler açıklamak için kullanılır. Ancak, bazı Gelişmiş senaryolar program kullanarak <xref:System.ServiceModel.Channels.Message> doğrudan sınıfı. Örneğin, kullanmak isteyebilirsiniz <xref:System.ServiceModel.Channels.Message> sınıfı:  
  
-   Seri hale getirme yerine giden ileti içeriği (örneğin, disk üzerindeki bir dosyadan doğrudan bir ileti oluşturma) oluşturma alternatif bir yol gerektiğinde [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] nesneleri.  
  
-   İçine seri durumdan yerine gelen ileti içeriği (örneğin, ham XML içeriği XSLT dönüştürmesi uygulamak istediğinizde) kullanarak, alternatif bir yol gerektiğinde [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] nesneleri.  
  
-   İleti içeriği ne olursa olsun genel bir şekilde iletilerle dağıtılacak gerektiğinde (örneğin, yönlendirme veya yönlendirici, yük dengeleyici veya bir yayımlama oluştururken İletileri iletirken-sistem abone).  
  
 Kullanmadan önce <xref:System.ServiceModel.Channels.Message> sınıfı, ile öğrenmeniz [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] veri aktarımı mimarisinde [veri aktarımı mimarisine genel bakış](../../../../docs/framework/wcf/feature-details/data-transfer-architectural-overview.md).  
  
 A <xref:System.ServiceModel.Channels.Message> veriler için genel amaçlı bir kapsayıcı olmakla birlikte, tasarımı tasarım SOAP protokolü iletinin yakından izler. Gibi bir ileti gövdesi ve üstbilgileri SOAP içinde bir ileti vardır. Üstbilgileri ek adlandırılmış veri kapsayıcıları içerirken ileti gövdesi gerçek yükü verilerini içerir. Gövde ve üst bilgileri okumak ve yazmak için kuralları farklı, örneğin üstbilgileri bellekte her zaman arabelleğe ve içinde erişilebilir gövdesi okuma yalnızca bir kez ve veri akışı ancak zaman, herhangi bir sayıda sipariş. Normalde, SOAP kullanırken, ileti gövdesi SOAP gövdesi eşlenen ve ileti üstbilgilerini SOAP üstbilgileri eşlenir.  
  
## <a name="using-the-message-class-in-operations"></a>İşlemlerinde ileti sınıfını kullanma  
 Kullanabileceğiniz <xref:System.ServiceModel.Channels.Message> sınıfının giriş parametresi olarak bir işlem, bir işlem veya her ikisi de dönüş değeri. Varsa <xref:System.ServiceModel.Channels.Message> kullanılan herhangi bir işlem, aşağıdaki kısıtlamalar geçerlidir:  
  
-   İşlemi içeremez `out` veya `ref` parametreleri.  
  
-   Olamaz birden fazla `input` parametresi. Parametresi varsa, ileti veya bir ileti sözleşmesi türü olmalıdır.  
  
-   Dönüş türü ya da olmalıdır `void`, `Message`, veya bir ileti sözleşme türü.  
  
 Aşağıdaki kod örneğinde geçerli işlem sözleşme içerir.  
  
 [!code-csharp[C_UsingTheMessageClass#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#1)]
 [!code-vb[C_UsingTheMessageClass#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#1)]  
  
## <a name="creating-basic-messages"></a>Temel iletileri oluşturuluyor  
 <xref:System.ServiceModel.Channels.Message> SAX statik `CreateMessage` temel iletileri oluşturmak için kullanabileceğiniz Fabrika yöntemleri.  
  
 Tüm `CreateMessage` aşırı ele türünde bir sürüm parametresi <xref:System.ServiceModel.Channels.MessageVersion> ileti için kullanılacak SOAP ve WS adresleme sürümleri gösterir. Aynı protokol sürümleri gelen iletiyi olarak kullanmak istiyorsanız, kullanabileceğiniz <xref:System.ServiceModel.OperationContext.IncomingMessageVersion%2A> özelliği <xref:System.ServiceModel.OperationContext> örneği elde <xref:System.ServiceModel.OperationContext.Current%2A> özelliği. Çoğu `CreateMessage` aşırı ileti için kullanılacak SOAP eylemi gösteren bir dize parametresi de vardır. Sürüm ayarlanabilir `None` SOAP Zarfı oluşturma; devre dışı bırakmak için ileti gövdesi yalnızca oluşur.  
  
## <a name="creating-messages-from-objects"></a>İletileri nesnelerden oluşturma  
 En temel `CreateMessage` yalnızca bir sürümü ve bir eylemi alır aşırı boş bir gövde ile bir ileti oluşturur. Başka bir aşırı ek bir alan <xref:System.Object> parametresi; bu, gövde belirtilen nesneyi seri hale getirilmiş gösterimini bir ileti oluşturur. Kullanım <xref:System.Runtime.Serialization.DataContractSerializer> serileştirilmesi için varsayılan ayarlarla. Farklı bir seri hale getirici kullanmak istediğiniz veya istediğiniz `DataContractSerializer` farklı şekilde yapılandırılmış kullanmak `CreateMessage` ayrıca alır aşırı bir `XmlObjectSerializer` parametresi.  
  
 Örneğin, bir nesne bir iletide döndürmek için aşağıdaki kodu kullanabilirsiniz.  
  
 [!code-csharp[C_UsingTheMessageClass#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#2)]
 [!code-vb[C_UsingTheMessageClass#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#2)]  
  
## <a name="creating-messages-from-xml-readers"></a>XML okuyuculardan iletileri oluşturuluyor  
 Vardır `CreateMessage` overloads süren bir <xref:System.Xml.XmlReader> veya bir <xref:System.Xml.XmlDictionaryReader> bir nesne yerine gövdesi için. Bu durumda, ileti gövdesi geçirilen XML okuyucusu okunurken oluşur XML içeriyor. Örneğin, aşağıdaki kod içeriği bir XML dosyasından okuma gövdesini içeren bir ileti döndürür.  
  
 [!code-csharp[C_UsingTheMessageClass#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#3)]
 [!code-vb[C_UsingTheMessageClass#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#3)]  
  
 Ayrıca, `CreateMessage` overloads süren bir <xref:System.Xml.XmlReader> veya bir <xref:System.Xml.XmlDictionaryReader> tüm ileti ve yalnızca gövde temsil eder. Bu aşırı ayrıca bir tamsayı olması `maxSizeOfHeaders` parametresi. Gerçekleşir iletisi oluşturulur ve bu parametre arabelleğe alma miktarını sınırlar hemen belleğe üstbilgileri her zaman arabelleğe alındı. XML bir hizmet reddi saldırısına olasılığını azaltmak için güvenilmeyen bir kaynaktan geliyorsa bu parametreyi güvenli bir değere ayarlamak önemlidir. XML okuyucuyu temsil eder iletinin SOAP ve WS adresleme sürümleri sürüm parametresi kullanılarak belirtilen sürümleri uyuşmalıdır.  
  
## <a name="creating-messages-with-bodywriter"></a>İletileri BodyWriter ile oluşturma  
 Bir `CreateMessage` alır aşırı bir `BodyWriter` ileti gövdesini açıklamak için örneği. A `BodyWriter` İleti gövdeleri nasıl oluşturulduğunu özelleştirmek için türetilmiş bir Özet sınıf. Kendi oluşturabilirsiniz `BodyWriter` türetilen İleti gövdeleri özel bir biçimde tanımlamak için sınıfı. Geçersiz kılmanız gerekir `BodyWriter.OnWriteBodyContents` yönteminin alan bir <xref:System.Xml.XmlDictionaryWriter>; bu yöntem gövde yazmaktan sorumludur.  
  
 Gövde yazıcılarının arabelleğe veya (akışı arabelleğe olmayan). Akış olanları içeriklerini yalnızca bir kez yazabilirsiniz sırada arabelleğe alınan gövde yazıcılarının zaman, herhangi bir sayıda içeriklerini yazabilirsiniz. `IsBuffered` Özelliği, Gövde yazıcısı veya arabelleğe alınıp alınmayacağını belirtir. Bu, Gövde yazıcısı için korumalı çağırarak ayarlayabileceğiniz `BodyWriter` alan oluşturucu bir `isBuffered` Boole parametresi. Gövde yazıcılarının arabelleğe gövde yazıcıdan bir arabelleğe alınan Gövde yazıcısı oluşturmayı destekler. Geçersiz kılabilirsiniz `OnCreateBufferedCopy` bu işlemi özelleştirmek için yöntem. Varsayılan olarak, XML içeren bir bellek içi arabellek tarafından döndürülen `OnWriteBodyContents` kullanılır. `OnCreateBufferedCopy`alan bir `maxBufferSize` tamsayı parametresi; bu yöntemi geçersiz kılarsanız, arabellek bu en yüksek boyuttan büyük oluşturmamalıdır.  
  
 `BodyWriter` SAX `WriteBodyContents` ve `CreateBufferedCopy` temelde olan yöntemler, geçici sarmalayıcıları ince `OnWriteBodyContents` ve `OnCreateBufferedCopy` yöntemleri, sırasıyla. Bu yöntemler bir arabelleğe Gövde yazıcısı birden çok kez erişmediğinden emin olmak için durum denetimi gerçekleştirin. Bu yöntemlerin doğrudan yalnızca özel oluşturulurken çağrılır `Message` türetilmiş sınıflar temel `BodyWriters`.  
  
## <a name="creating-fault-messages"></a>Hata iletileri oluşturma  
 Belirli kullanabilirsiniz `CreateMessage` SOAP oluşturmak için aşırı hata iletileri. En temel bu alır, bir <xref:System.ServiceModel.Channels.MessageFault> hataya tanımlayan nesne. Diğer aşırı yüklemeler kolaylık olması için sağlanmıştır. İlk gibi aşırı alır bir `FaultCode` ve nedeni dize ve oluşturan bir `MessageFault` kullanarak `MessageFault.CreateFault` bu bilgileri kullanarak. Diğer aşırı ayrıntı nesnesini alır ve aynı zamanda buna ileten `CreateFault` hata kodu ve açıklaması ile birlikte. Örneğin, aşağıdaki işlemi bir hata döndürür.  
  
 [!code-csharp[C_UsingTheMessageClass#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#4)]
 [!code-vb[C_UsingTheMessageClass#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#4)]  
  
## <a name="extracting-message-body-data"></a>İleti gövdesi veri çıkarma  
 `Message` Sınıfı, kendi gövdesinden bilgileri ayıklanıyor birkaç yolu destekler. Bunlar aşağıdaki kategorilerde sınıflandırılabilir:  
  
-   Aynı anda bir XML yazıcı yazılan tüm ileti gövdesi alınıyor. Bu olarak adlandırılır *ileti yazmayı*.  
  
-   Bir XML okuyucusu ileti gövdesi alınıyor. Bu, daha sonra erişimi ileti gövdesi parça tarafından-parçası gerektiği gibi sağlar. Bu olarak adlandırılır *bir ileti okunurken*.  
  
-   Kendi gövde dahil olmak üzere tüm ileti bir bellek içi arabelleğe kopyalanabilir <xref:System.ServiceModel.Channels.MessageBuffer> türü. Bu olarak adlandırılır *bir ileti kopyalama*.  
  
 Gövdesini erişebileceği bir `Message` nasıl erişilir bağımsız olarak yalnızca bir kez,. Bir ileti nesnesi olan bir `State` başlangıçta oluşturuldu olarak ayarlama özelliği. Önceki listede açıklanan üç erişim yöntemleri durumu yazılan, okuma ve kopyalandı, sırasıyla ayarlayın. Ayrıca, bir `Close` yöntemi ayarlayabilirsiniz durumu kapalı olarak ileti gövdesi içeriği artık gerekli olduğunda. İleti gövdesi yalnızca oluşturulan durumda erişilebilir ve durumu değiştikten sonra oluşturulan durumuna geri dönmek için yolu yoktur.  
  
## <a name="writing-messages"></a>Yazma iletileri  
 <xref:System.ServiceModel.Channels.Message.WriteBodyContents%28System.Xml.XmlDictionaryWriter%29> Yöntemi Yazar gövdesi içeriğini bir verilen `Message` verilen XML yazıcıyı örneğine. <xref:System.ServiceModel.Channels.Message.WriteBody%2A> Yöntemi yaptığı aynı uygun sarmalayıcı öğesinde gövdesi içeriğini barındırır dışında (örneğin, <`soap:body`>). Son olarak, <xref:System.ServiceModel.Channels.Message.WriteMessage%2A> kaydırma dahil olmak üzere tüm ileti yazar SOAP zarfını ve üstbilgileri. SOAP kapalıysa (sürüm `MessageVersion.None`), tüm üç yöntem aynı işlevi görür: ileti gövdesi içeriğini yazma.  
  
 Örneğin, bir dosyaya gelen ileti gövdesini çıkışı aşağıdaki kodu yazar.  
  
 [!code-csharp[C_UsingTheMessageClass#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#5)]
 [!code-vb[C_UsingTheMessageClass#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#5)]  
  
 İki ek yardımcı yöntemler belirli SOAP başlangıç öğesi etiketleri yazma. Bu yöntemler ileti gövdesi erişmemesi ve bu nedenle bunlar ileti durumu değiştirme. Bu güncelleştirmeler şunlardır:  
  
-   <xref:System.ServiceModel.Channels.Message.WriteStartBody%2A>Örneğin, başlangıç body öğesi Yazar `<soap:Body>`.  
  
-   <xref:System.ServiceModel.Channels.Message.WriteStartEnvelope%2A>Örneğin, başlangıç envelope öğesi Yazar `<soap:Envelope>`.  
  
 Öğe etiketleri karşılık gelen son yazmak için arama `WriteEndElement` karşılık gelen XML yazıcıda. Bu yöntemler nadiren doğrudan denir.  
  
## <a name="reading-messages"></a>İletileri okuma  
 İleti gövdesini okumak için birincil yolu çağırmaktır <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A>. Geri alma bir <xref:System.Xml.XmlDictionaryReader> ileti gövdesini okumak için kullanabilirsiniz. Unutmayın <xref:System.ServiceModel.Channels.Message> okuma durumu geçişleri hemen <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> denir ve değil döndürülen XML Okuyucu kullandığınızda.  
  
 <xref:System.ServiceModel.Channels.Message.GetBody%2A> Yöntemi de ileti gövdesi yazılmış bir nesne olarak erişmesine olanak sağlar. Dahili olarak, bu yöntemi kullanır `GetReaderAtBodyContents`, ve ayrıca ileti durumu geçişleri <xref:System.ServiceModel.Channels.MessageState.Read> durumu (bkz: <xref:System.ServiceModel.Channels.Message.State%2A> özelliği).  
  
 Denetlemek için iyi bir uygulamadır <xref:System.ServiceModel.Channels.Message.IsEmpty%2A> özelliği, içinde olduğu bu durum ileti gövdesi boş ve <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> oluşturur bir <xref:System.InvalidOperationException>. Alınan ileti (örneğin, yanıt) etkinleştirilmişse, ayrıca, aynı zamanda denetlemek isteyebilirsiniz <xref:System.ServiceModel.Channels.Message.IsFault%2A>, iletinin bir hata içerip içermediğini belirtir.  
  
 En temel aşırı yüklemesini <xref:System.ServiceModel.Channels.Message.GetBody%2A> türü (genel parametresi tarafından belirtilir) kullanarak bir örneğine ileti gövdesi seri durumdan çıkarır bir <xref:System.Runtime.Serialization.DataContractSerializer> varsayılan ayarlarla ve yapılandırılmış <xref:System.Runtime.Serialization.DataContractSerializer.MaxItemsInObjectGraph%2A> kota devre dışı. Farklı serileştirme motoruna kullanın ya da yapılandırmak isteyip istemediğinizi `DataContractSerializer` bir varsayılan olmayan şekilde kullanma <xref:System.ServiceModel.Channels.Message.GetBody%2A> alan aşırı bir <xref:System.Runtime.Serialization.XmlObjectSerializer>.  
  
 Örneğin, aşağıdaki kodu verileri seri hale getirilmiş bir içeren bir ileti gövdesinden ayıklar `Person` nesne ve kişinin adını yazdırır.  
  
 [!code-csharp[C_UsingTheMessageClass#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#6)]
 [!code-vb[C_UsingTheMessageClass#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#6)]  
  
## <a name="copying-a-message-into-a-buffer"></a>Bir ileti bir arabelleğe kopyalama  
 Bazen ileti gövdesi birden çok kez, örneğin erişmek için bir yayımcı abone sisteminin parçası olarak birden çok varış yeri için aynı iletisini iletmek için gerekli değildir. Bu durumda, bellekte (gövdesi dahil) tüm ileti arabellek gereklidir. Bunu çağırarak yapmak <xref:System.ServiceModel.Channels.Message.CreateBufferedCopy%28System.Int32%29>. Bu yöntem, en büyük arabellek boyutu temsil eder ve bir arabellek bu boyuttan büyük oluşturan bir tamsayı parametresini alır. İleti güvenilmeyen bir kaynaktan geliyorsa bu güvenli bir değere ayarlamak önemlidir.  
  
 Arabellek olarak döndürülür bir <xref:System.ServiceModel.Channels.MessageBuffer> örneği. Çeşitli şekillerde arabelleği erişebilir. Birincil yolu çağırmaktır <xref:System.ServiceModel.Channels.Message.CreateMessage%2A> oluşturmak için `Message` arabellekteki örnekleri.  
  
 Arabellekteki verilere erişmek için bir başka yolu uygulamaktır <xref:System.Xml.XPath.IXPathNavigable> arabirim <xref:System.ServiceModel.Channels.MessageBuffer> sınıf temel alınan XML doğrudan erişmek için uygular. Bazı <xref:System.ServiceModel.Channels.MessageBuffer.CreateNavigator%2A> aşırı oluşturmanıza izin <xref:System.Xml.XPath> bir düğüm kota tarafından korunan gezginlerini ziyaret edilebilir XML düğüm sayısını sınırlandırma. Bu, uzun işleme zamanı temel alınarak hizmet reddi saldırılarını önlemeye yardımcı olur. Bu teklif, varsayılan olarak devre dışıdır. Bazı `CreateNavigator` aşırı boşluk XML'de nasıl işleneceğini belirtmenize olanak tanır kullanarak <xref:System.Xml.XmlSpace> varsayılan olan ile numaralandırma `XmlSpace.None`.  
  
 İleti arabelleği içeriğine erişmek için son kullanarak akış içeriğini yazmak için yoludur <xref:System.ServiceModel.Channels.Message.WriteMessage%2A>.  
  
 Aşağıdaki örnek çalışma sürecini gösterir bir `MessageBuffer`: gelen ileti birden çok alıcıya iletilen ve bir dosyaya oturum. İleti gövdesi sonra yalnızca bir kez erişilebildiğinden arabelleğe alma olmadan bu mümkün değildir.  
  
 [!code-csharp[C_UsingTheMessageClass#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#7)]
 [!code-vb[C_UsingTheMessageClass#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#7)]  
  
 `MessageBuffer` Sınıfı eşitlenmeyeceği diğer üyeleri sahiptir. <xref:System.ServiceModel.Channels.MessageBuffer.Close%2A> Yöntemi arabellek içeriği artık gerekli olduğunda kaynakları serbest bırakmak için çağrılabilir. <xref:System.ServiceModel.Channels.MessageBuffer.BufferSize%2A> Özelliği ayrılan arabellek boyutu döndürür. <xref:System.ServiceModel.Channels.MessageBuffer.MessageContentType%2A> Özelliği ileti MIME içerik türünü döndürür.  
  
## <a name="accessing-the-message-body-for-debugging"></a>Hata ayıklama için ileti gövdesi erişme  
 Hata ayıklama amacıyla çağırabilirsiniz <xref:System.ServiceModel.Channels.Message.ToString%2A> iletinin gösterimini bir dize olarak almak için yöntemi. Bu gösterim genellikle metin Kodlayıcı ile kodlanmış, XML İnsan okunabilirlik için daha iyi biçimlendirilmiş olması ancak bu bir ileti kablo görünür şekilde eşleşir. Bunun tek istisnası, ileti gövdesi ' dir. Gövde yalnızca bir kez okuyabilir ve `ToString` ileti durumu değiştirmez. Bu nedenle, `ToString` yöntemi gövdesi erişmek kuramamış olabilir ve ileti gövdesi yerine bir yer tutucu (örneğin, "..." veya üç nokta) yerine. Bu nedenle, kullanmayın `ToString` ileti gövdesi içeriğini önemliyse iletilerini günlüğe kaydetmek için.  
  
## <a name="accessing-other-message-parts"></a>Diğer ileti bölümleri erişme  
 Çeşitli özellikler, ileti gövdesi içeriğini dışında hakkında bilgilere erişmek için sağlanır. Ancak, ileti kapatıldıktan sonra bu çağrılamaz:  
  
-   <xref:System.ServiceModel.Channels.Message.Headers%2A> Özelliği, ileti üstbilgilerini temsil eder. Bu konunun devamındaki "Üstbilgileri ile çalışma" bölümüne bakın.  
  
-   <xref:System.ServiceModel.Channels.Message.Properties%2A> Özelliği iletisine adlandırılmış veri ileti gönderildiğinde genellikle gösterilen değil parçalarıdır ileti özelliklerini temsil eder. Bu konunun devamındaki "Özellikler ile çalışma" bölümüne bakın.  
  
-   <xref:System.ServiceModel.Channels.Message.Version%2A> Özelliği iletiyle ilişkilendirilmiş SOAP ve WS adresleme sürümünü gösterir veya `None` SOAP devre dışı.  
  
-   <xref:System.ServiceModel.Channels.Message.IsFault%2A> Özelliği döndürür `true` ileti bir SOAP hatası iletisi ise.  
  
-   <xref:System.ServiceModel.Channels.Message.IsEmpty%2A> Özelliği döndürür `true` ileti boşsa.  
  
 Kullanabileceğiniz <xref:System.ServiceModel.Channels.Message.GetBodyAttribute%28System.String%2CSystem.String%29> gövde sarmalayıcı öğe üzerinde belirli bir öznitelik erişmek için yöntem (örneğin, `<soap:Body>`) belirli ad ve ad alanı tarafından tanımlanan. Bu tür bir öznitelik bulunmazsa `null` döndürülür. Bu yöntem yalnızca çağrılabilir `Message` (ileti gövdesi yok henüz erişildikten olduğunda) oluşturulan bir durumda.  
  
## <a name="working-with-headers"></a>Üst bilgileri ile çalışma  
 A `Message` adlı adlandırılmış XML parçaları herhangi bir sayıda içerebilir *üstbilgileri*. Her parça normalde bir SOAP üstbilgi eşler. Üstbilgiler yoluyla erişilir `Headers` türündeki özelliği <xref:System.ServiceModel.Channels.MessageHeaders>. <xref:System.ServiceModel.Channels.MessageHeaders>koleksiyonudur <xref:System.ServiceModel.Channels.MessageHeaderInfo> nesneleri ve tek tek üstbilgileri erişilebilir aracılığıyla kendi <xref:System.Collections.IEnumerable> arabirimi veya kendi dizinleyici aracılığıyla. Örneğin, aşağıdaki kod tüm üstbilgilerinde adlarını listeler bir `Message`.  
  
 [!code-csharp[C_UsingTheMessageClass#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#8)]
 [!code-vb[C_UsingTheMessageClass#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#8)]  
  
#### <a name="adding-removing-finding-headers"></a>Ekleme, kaldırma, bulma üstbilgileri  
 Yeni bir üstbilgi kullanarak tüm mevcut üstbilgileri sonunda ekleyebilirsiniz <xref:System.ServiceModel.Channels.MessageHeaders.Add%2A> yöntemi. Kullanabileceğiniz <xref:System.ServiceModel.Channels.MessageHeaders.Insert%2A> belirli bir dizinden bir başlık eklemek için yöntem. Varolan üstbilgileri eklenen öğe için gölgeye. Üstbilgiler kendi dizini göre sıralanır ve ilk kullanılabilir dizini 0'dır. Çeşitli kullanabilirsiniz <xref:System.ServiceModel.Channels.MessageHeaders.CopyHeadersFrom%2A> üstbilgileri farklı bir eklemek için yöntemi aşırı `Message` veya `MessageHeaders` örneği. Başkalarının bunların tümünün kopyalarken bazı aşırı tek tek tek üstbilgi kopyalayın. <xref:System.ServiceModel.Channels.MessageHeaders.Clear%2A> Yöntemi, tüm üstbilgileri kaldırır. <xref:System.ServiceModel.Channels.MessageHeaders.RemoveAt%2A> Yöntemi (tüm üstbilgileri sonra kaydırma) belirli bir dizine üstbilgi kaldırır. <xref:System.ServiceModel.Channels.MessageHeaders.RemoveAll%2A> Yöntemi, bir belirli ve ad alanına sahip tüm başlıkları kaldırır.  
  
 Kullanarak bir belirli üst bilgisi almak <xref:System.ServiceModel.Channels.MessageHeaders.FindHeader%2A> yöntemi. Bu yöntem adı ve bulmak için üst bilgisi ad alanını alır ve dizinini döndürür. Üstbilgi birden çok kez ortaya çıkarsa, bir özel durum oluşur. Üstbilgi bulunmazsa -1 döndürür.  
  
 SOAP üstbilgi modelinde üstbilgileri olabilir bir `Actor` üstbilgisinin hedeflenen alıcı belirten değer. En temel `FindHeader` aşırı yalnızca ileti ultimate alıcısı için hedeflenen üstbilgileri arar. Ancak, başka bir aşırı, hangi belirtmenize olanak tanır `Actor` değerleri aramada dahil edilir. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]SOAP belirtimi.  
  
 A <xref:System.ServiceModel.Channels.MessageHeaders.CopyTo%28System.ServiceModel.Channels.MessageHeaderInfo%5B%5D%2CSystem.Int32%29> yöntemi sağlanan üstbilgileri kopyalamak için bir <xref:System.ServiceModel.Channels.MessageHeaders> bir dizi koleksiyona <xref:System.ServiceModel.Channels.MessageHeaderInfo> nesneleri.  
  
 Üstbilgi XML verilerine erişmek için çağırabilirsiniz <xref:System.ServiceModel.Channels.MessageHeaders.GetReaderAtHeader%2A> ve özel üstbilgi dizini için bir XML okuyucu döndür. Üst bilgi içeriği nesne seri durumdan istiyorsanız kullanın <xref:System.ServiceModel.Channels.MessageHeaders.GetHeader%60%601%28System.Int32%29> veya diğer aşırı yüklemeler biri. En temel alan aşırı kullanarak üstbilgileri seri durumdan <xref:System.Runtime.Serialization.DataContractSerializer> varsayılan olarak yapılandırılmış yolu. Farklı bir seri hale getirici veya farklı bir yapılandırmasını kullanmak isteyip istemediğinizi `DataContractSerializer`, ele alan aşırı birini kullanın bir `XmlObjectSerializer`. Ayrıca üstbilgi adı, ad ve isteğe bağlı olarak bir listesini alın aşırı olan `Actor` değerleri yerine bir dizin; bu bir birleşimidir `FindHeader` ve `GetHeader`.  
  
## <a name="working-with-properties"></a>Özellikleri ile çalışma  
 A `Message` örneği rasgele bir rastgele türler adlandırılmış nesnelerin sayısı içerebilir. Bu koleksiyon üzerinden erişilen `Properties` türündeki özelliği `MessageProperties`. Koleksiyon uygulayan <xref:System.Collections.Generic.IDictionary%602> arabirim ve eşlemeyi gibi davranır <xref:System.String> için <xref:System.Object>. Genellikle özellik değerlerini doğrudan ileti hattaki herhangi bir kısmını eşlemek değil, ancak bunun yerine çeşitli kanallar için çeşitli ileti işleme ipuçları sağlayan [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kanal yığın veya <xref:System.ServiceModel.Channels.MessageHeaders.CopyTo%28System.ServiceModel.Channels.MessageHeaderInfo%5B%5D%2CSystem.Int32%29> hizmet çerçevesi. Bir örnek için bkz: [veri aktarımına mimari genel bakış](../../../../docs/framework/wcf/feature-details/data-transfer-architectural-overview.md).  
  
## <a name="inheriting-from-the-message-class"></a>İleti sınıfından devralma  
 Yerleşik türler kullanılarak oluşturulan olursa `CreateMessage` değil gereksinimlerinizi karşılayacak, türeyen bir sınıf oluşturun `Message` sınıfı.  
  
### <a name="defining-the-message-body-contents"></a>İleti gövdesi içeriğini tanımlama  
 Üç birincil teknikleri mevcut bir ileti gövdesi içinde verilerine erişmek için: yazma, okuma ve bir arabelleğine kopyalanıyor. Bu işlemler sonuçta neden <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%2A>, <xref:System.ServiceModel.Channels.Message.OnGetReaderAtBodyContents%2A>, ve <xref:System.ServiceModel.Channels.Message.OnCreateBufferedCopy%2A> , sırasıyla türetilmiş sınıfınız çağrılan yöntemler `Message`. Temel `Message` sınıfı garanti bu yöntemlerden sadece birini her biri için çağrılır `Message` örneği ve onu birden çok kez çağrılmaz olduğunu. Taban sınıfı, aynı zamanda kapatılan bir mesaj yöntemleri adlı değil sağlar. Uygulamanızda ileti durumunu izlemek için gerek yoktur.  
  
 <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%2A>soyut bir yöntemdir ve uygulanması gerekir. İleti gövdesi içeriğini tanımlamak için en basit yolu, bu yöntemi kullanarak yazmaktır. Örneğin, aşağıdaki iletiyi 1'den 100.000 rastgele sayılar 20 içerir.  
  
 [!code-csharp[C_UsingTheMessageClass#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#9)]
 [!code-vb[C_UsingTheMessageClass#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#9)]  
  
 `OnGetReaderAtBodyContents` Ve `OnCreateBufferedCopy` yöntemleri için çoğu durumda iş varsayılan uygulamaları vardır. Varsayılan uygulamaları çağrısı `OnWriteBodyContents`sonuçları arabellek ve iş ile elde edilen arabellek. Ancak, bazı durumlarda bu yeterli olmayabilir. Önceki örnekte arzu olmayabilir arabelleğe alınan 100.000 XML öğelerinin ileti sonuçlarında okunuyor. Geçersiz kılma isteyebilirsiniz `OnGetReaderAtBodyContents` özel döndürülecek `XmlDictionaryReader` türetilen rastgele sayıları yukarı hizmet sınıfı. Daha sonra geçersiz `OnWriteBodyContents` okuyucu kullanmak için `OnGetReaderAtBodyContents` özelliği döndürür, aşağıdaki örnekte gösterildiği gibi.  
  
 [!code-csharp[C_UsingTheMessageClass#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#10)]
 [!code-vb[C_UsingTheMessageClass#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#10)]  
  
 Benzer şekilde, geçersiz kılmak istediğiniz durumlarda `OnCreateBufferedCopy` kendi döndürülecek `MessageBuffer` türetilmiş sınıf.  
  
 İleti gövdesi içeriğini sağlamanın yanı sıra, türetilen ileti sınıfı ayrıca geçersiz kılmanız gerekir `Version`, `Headers`, ve `Properties` özellikleri.  
  
 Bir iletinin bir kopyasını oluşturursanız, kopya özgün ileti üstbilgileri kullandığına dikkat edin.  
  
### <a name="other-members-that-can-be-overridden"></a>Geçersiz kılınabilir diğer üyeleri  
 Geçersiz kılabilirsiniz <xref:System.ServiceModel.Channels.Message.OnWriteStartEnvelope%2A>, <xref:System.ServiceModel.Channels.Message.OnWriteStartHeaders%2A>, ve <xref:System.ServiceModel.Channels.Message.OnWriteStartBody%2A> nasıl SOAP Zarfı, SOAP üstbilgileri ve SOAP gövdesi öğesi başlangıç etiketleri belirtmek için yöntemlerini yazılır. Bunlar normalde karşılık `<soap:Envelope>`, `<soap:Header>`, ve `<soap:Body>`. Bu yöntemler IF şeyi yazması gerektiğini normalde `Version` özelliği döndürür `MessageVersion.None`.  
  
> [!NOTE]
>  Varsayılan uygulaması `OnGetReaderAtBodyContents` çağrıları `OnWriteStartEnvelope` ve `OnWriteStartBody` çağırmadan önce `OnWriteBodyContents` ve sonuçları arabelleğe alma. Üstbilgiler yazılmaz.  
  
 Geçersiz kılma <xref:System.ServiceModel.Channels.Message.OnWriteMessage%2A> kendi yapıları tüm ileti yapılandırılmıştır şeklini değiştirmek için yöntem. `OnWriteMessage` Yöntemi çağrılır <xref:System.ServiceModel.Channels.Message.WriteMessage%2A> ve varsayılan <xref:System.ServiceModel.Channels.Message.OnCreateBufferedCopy%2A> uygulaması. Bu geçersiz kılma Not <xref:System.ServiceModel.Channels.Message.WriteMessage%2A> en iyi yöntem değildir. Uygun geçersiz kılmak iyidir `On` yöntemleri (örneğin, <xref:System.ServiceModel.Channels.Message.OnWriteStartEnvelope%2A>, <xref:System.ServiceModel.Channels.Message.OnWriteStartHeaders%2A>, ve <xref:System.ServiceModel.Channels.BodyWriter.OnWriteBodyContents%2A>.  
  
 Geçersiz kılma <xref:System.ServiceModel.Channels.Message.OnBodyToString%2A> , ileti gövdesi hata ayıklama sırasında nasıl temsil geçersiz kılmak için. Üç nokta temsil eder ("...") varsayılandır. İleti durumu kapalı dışında bir şey olduğunda bu yöntem birden çok kez çağrılamaz unutmayın. Bu yöntemin bir uygulaması, hiçbir zaman (örneğin, yalnızca ileri akışından okuma) yalnızca bir kez gerçekleştirilmesi gereken herhangi bir eylem neden olmaz.  
  
 Geçersiz kılma <xref:System.ServiceModel.Channels.Message.OnGetBodyAttribute%2A> SOAP gövdesi öğede öznitelikleri erişmesine izin vermek için yöntem. Bu yöntem herhangi bir sayıda kez çağrılabilir ancak `Message` temel türü ileti oluşturulan durumda olduğunda, yalnızca çağrıldığından emin güvence altına alır. Bir uygulama durumunda denetlemek için gerekli değildir. Varsayılan uygulama her zaman döndürür `null`, gövde öğede özniteliklere olduğunu gösterir.  
  
 Varsa, `Message` nesne, tüm özel temizleme gerçekleştirmelisiniz, ileti gövdesi artık gerekli olmadığında, geçersiz kılabilirsiniz <xref:System.ServiceModel.Channels.Message.OnClose%2A>. Varsayılan uygulama hiçbir şey yapmaz.  
  
 `IsEmpty` Ve `IsFault` özellikleri geçersiz. Varsayılan olarak, her ikisi de dönmek `false`.
