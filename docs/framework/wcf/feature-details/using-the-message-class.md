---
title: İleti Sınıfını Kullanma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d1d62bfb-2aa3-4170-b6f8-c93d3afdbbed
ms.openlocfilehash: d9b1c1242fe2686a66e41b777f904a71898159ea
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2019
ms.locfileid: "58409607"
---
# <a name="using-the-message-class"></a>İleti Sınıfını Kullanma
<xref:System.ServiceModel.Channels.Message> Sınıfı, temel Windows Communication Foundation (WCF). İstemciler ve hizmetler arasındaki tüm iletişim sonuçta sonuçlanır <xref:System.ServiceModel.Channels.Message> örnekleri için gönderilen ve alınan.  
  
 Genellikle ile etkileşime değil <xref:System.ServiceModel.Channels.Message> doğrudan sınıf. Bunun yerine, veri sözleşmeleri, ileti sözleşmeleri ve işlem sözleşmeleri gibi WCF service model yapıları, gelen ve giden iletileri tanımlamak için kullanılır. Ancak, bazı Gelişmiş senaryolar program kullanarak <xref:System.ServiceModel.Channels.Message> doğrudan sınıf. Örneğin, kullanmak isteyebilirsiniz <xref:System.ServiceModel.Channels.Message> sınıfı:  
  
-   Seri hale getirme yerine (örneğin, bir dosyanın disk üzerinde doğrudan bir ileti oluşturma) giden ileti içeriği oluşturma alternatif bir yolu gerektiğinde [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] nesneleri.  
  
-   Bir alternatif bir yolu içine seri durumdan çıkarılırken yerine (örneğin, ham XML içeriği XSLT dönüştürmesi uygulamak istediğinizde) gelen ileti içeriği kullanma gerektiğinde [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] nesneleri.  
  
-   İleti içeriği ne olursa olsun genel bir şekilde iletilerle dağıtılacak gerektiğinde (örneğin, yönlendirme veya yönlendirici, yük dengeleyici veya bir yayımlama oluştururken iletirken-sistem abone).  
  
 Kullanmadan önce <xref:System.ServiceModel.Channels.Message> sınıfı, WCF veri aktarımı mimaride planladığınızdan [veri aktarımı mimarisine genel bakış](../../../../docs/framework/wcf/feature-details/data-transfer-architectural-overview.md).  
  
 A <xref:System.ServiceModel.Channels.Message> veri için genel amaçlı bir kapsayıcı, ancak tasarımı, SOAP protokolü iletisinde tasarımını yakından takip eder. SOAP içinde olduğu gibi bir ileti hem bir ileti gövdesi hem de üst bilgileri içerir. Ek adlandırılmış veri kapsayıcı üstbilgileri içerirken ileti gövdesi gerçek yükü verileri içerir. Kural gövdesi ve üst bilgileri okumak ve yazmak için farklıdır, örneğin, üst bilgileri her zaman bellekte arabelleğe alınır ve içinde erişilebilir zaman, herhangi bir sayıda sipariş gövdesi yalnızca bir kez okunabilir ve akışla. Normalde, SOAP kullanırken, ileti gövdesi SOAP gövdesi için eşlenir ve ileti üstbilgilerini SOAP üstbilgileri eşleştirilir.  
  
## <a name="using-the-message-class-in-operations"></a>İşlemlerinde ileti sınıfını kullanma  
 Kullanabileceğiniz <xref:System.ServiceModel.Channels.Message> sınıfının giriş parametresi olarak bir işlem, bir işlem veya her ikisi de dönüş değeri. Varsa <xref:System.ServiceModel.Channels.Message> kullanılan herhangi bir işlem, aşağıdaki kısıtlamalar uygulanır:  
  
-   İşlemi içeremez `out` veya `ref` parametreleri.  
  
-   Olamaz birden fazla `input` parametresi. Parametre varsa, ileti ya da ileti anlaşması türü olmalıdır.  
  
-   Dönüş türü olmalıdır `void`, `Message`, ya da sözleşme türü bir ileti.  
  
 Aşağıdaki kod örneği, geçerli işlem anlaşması içeriyor.  
  
 [!code-csharp[C_UsingTheMessageClass#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#1)]
 [!code-vb[C_UsingTheMessageClass#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#1)]  
  
## <a name="creating-basic-messages"></a>Temel iletileri oluşturuluyor  
 <xref:System.ServiceModel.Channels.Message> SAX statik `CreateMessage` temel iletileri oluşturmak için kullanabileceğiniz Fabrika yöntemleri.  
  
 Tüm `CreateMessage` aşırı ele türünde bir sürüm parametresi <xref:System.ServiceModel.Channels.MessageVersion> ileti için kullanılacak SOAP ve WS-Addressing sürümlerini gösterir. Gelen ileti aynı protokol sürümleri kullanmak istiyorsanız, kullanabileceğiniz <xref:System.ServiceModel.OperationContext.IncomingMessageVersion%2A> özelliği <xref:System.ServiceModel.OperationContext> örneği öğesinden alınan <xref:System.ServiceModel.OperationContext.Current%2A> özelliği. Çoğu `CreateMessage` aşırı yüklemeleri, ileti için kullanılacak SOAP eylemi belirten bir dize parametresi de vardır. Sürüm ayarlanabilir `None` SOAP Zarfı oluşturma;'devre dışı bırakmak için ileti gövdesi yalnızca oluşur.  
  
## <a name="creating-messages-from-objects"></a>Nesnelerden iletileri oluşturuluyor  
 En temel `CreateMessage` yalnızca bir sürümü ve bir eylem alan aşırı yüklemesini boş gövdesi bir ileti oluşturur. Başka bir aşırı ek bir alan <xref:System.Object> parametresi yok; Bu, gövde verilen nesne seri hale getirilmiş temsili bir ileti oluşturur. Kullanım <xref:System.Runtime.Serialization.DataContractSerializer> Serileştirmenin varsayılan ayarlarla. Farklı bir serileştirici kullanmak istediğiniz veya istemediğiniz `DataContractSerializer` farklı şekilde yapılandırılmış, kullanın `CreateMessage` ayrıca alan aşırı yüklemesini bir `XmlObjectSerializer` parametresi.  
  
 Örneğin, bir ileti nesneyi döndürmek için aşağıdaki kodu kullanabilirsiniz.  
  
 [!code-csharp[C_UsingTheMessageClass#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#2)]
 [!code-vb[C_UsingTheMessageClass#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#2)]  
  
## <a name="creating-messages-from-xml-readers"></a>XML okuyucular iletileri oluşturuluyor  
 Vardır `CreateMessage` aşırı süren bir <xref:System.Xml.XmlReader> veya <xref:System.Xml.XmlDictionaryReader> bir nesne yerine gövdesi için. Bu durumda, ileti gövdesi dosyasından okurken geçirilen XML okuyucusundan sonuçları XML içeriyor. Örneğin, aşağıdaki kod içeriği bir XML dosyasından okuma gövdesini içeren bir ileti döndürür.  
  
 [!code-csharp[C_UsingTheMessageClass#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#3)]
 [!code-vb[C_UsingTheMessageClass#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#3)]  
  
 Ayrıca, vardır `CreateMessage` aşırı süren bir <xref:System.Xml.XmlReader> veya bir <xref:System.Xml.XmlDictionaryReader> temsil eden tüm ileti ve yalnızca gövdesi. Bu aşırı yüklemeler ayrıca bir tamsayı olması `maxSizeOfHeaders` parametresi. Üst bilgileri, her zaman yer alan bir ileti oluşturulur ve bu parametre, arabelleğe alma miktarını sınırlar sürede belleğe arabelleğe alınır. XML bir hizmet reddi saldırısı olasılığını azaltmak için güvenilmeyen bir kaynaktan geliyorsa, bu parametre için güvenli bir değer ayarlamak önemlidir. XML okuyucuyu temsil eder iletinin SOAP ve WS-Addressing sürümleri, sürüm parametresi kullanılarak belirtilen sürümleri eşleşmelidir.  
  
## <a name="creating-messages-with-bodywriter"></a>İletileri ile BodyWriter oluşturuluyor  
 Bir `CreateMessage` alır aşırı bir `BodyWriter` iletisinin gövdesini açıklamak için örneği. A `BodyWriter` İleti gövdeleri nasıl oluşturulduğunu özelleştirmek için türetilmiş bir soyut sınıftır. Kendi oluşturabilirsiniz `BodyWriter` türetilmiş sınıf İleti gövdeleri özel bir şekilde tanımlamak için. Geçersiz kılmanız gerekir `BodyWriter.OnWriteBodyContents` gereken yöntemini bir <xref:System.Xml.XmlDictionaryWriter>; bu yöntem gövdesi yazmaktan sorumludur.  
  
 Gövde yazıcılar arabelleğe veya (akışı arabelleğe olmayan). Akış olanları, içeriği yalnızca bir kez yazabilirsiniz sırasında arabelleğe alınan gövdesi yazıcıları zaman, herhangi bir sayıda içeriklerini yazabilirsiniz. `IsBuffered` Özelliği bir Gövde yazıcısı veya arabelleğe alınıp alınmayacağını belirtir. Bu, Gövde yazıcısı için korumalı çağırarak ayarlayabileceğiniz `BodyWriter` alan oluşturucu bir `isBuffered` Boole parametresi. Gövde yazarları, arabelleğe gövdesi yazıcıdan arabelleğe alınan Gövde yazıcısı oluşturmayı destekler. Geçersiz kılabilirsiniz `OnCreateBufferedCopy` bu işlemi özelleştirmek için yöntemi. Varsayılan olarak, XML içeren bir bellek içi arabellek tarafından döndürülen `OnWriteBodyContents` kullanılır. `OnCreateBufferedCopy` alan bir `maxBufferSize` tam sayı parametresi; bu yöntemi geçersiz kılarsanız, arabellekler bu maksimum boyutu daha büyük oluşturmamalıdır.  
  
 `BodyWriter` Sağlar sınıfını `WriteBodyContents` ve `CreateBufferedCopy` temelde olan yöntemler, ince çevresinde sarmalayıcılar `OnWriteBodyContents` ve `OnCreateBufferedCopy` yöntemleri, sırasıyla. Bu yöntemler bir arabelleğe Gövde yazıcısı birden çok kez erişmediğinden emin olmak için durum denetimi gerçekleştirin. Yalnızca özel oluştururken, bu yöntemleri doğrudan çağrılır `Message` türetilmiş sınıflar temel `BodyWriters`.  
  
## <a name="creating-fault-messages"></a>Hata iletileri oluşturuluyor  
 Belirli kullanabileceğiniz `CreateMessage` SOAP oluşturmak için aşırı yüklemeleri hata iletileri. En temel bu alır, bir <xref:System.ServiceModel.Channels.MessageFault> hata tanımlayan nesne. Diğer aşırı yüklemeler, kolaylık olması için sağlanmıştır. İlk aşırı yükleme gibi alır bir `FaultCode` ve neden dize ve oluşturan bir `MessageFault` kullanarak `MessageFault.CreateFault` bu bilgileri kullanarak. Diğer aşırı bir ayrıntı nesnesini alır ve ayrıca geçirir `CreateFault` hata kodu ve nedeni. Örneğin, aşağıdaki işlemi bir hata döndürür.  
  
 [!code-csharp[C_UsingTheMessageClass#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#4)]
 [!code-vb[C_UsingTheMessageClass#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#4)]  
  
## <a name="extracting-message-body-data"></a>İleti gövde verilerini ayıklama  
 `Message` Sınıfı, kendi gövdesinden bilgilerini ayıklama birçok yolu destekler. Bunlar aşağıdaki kategoride sınıflandırılabilir:  
  
-   Tek seferde bir XML yazıcısı için yazılan tüm ileti gövdesi alınıyor. Bu olarak adlandırılır *bir iletiyi yazmanın*.  
  
-   Bir XML okuyucusu ileti gövdesi alınıyor. Bu, gerektiği gibi ileti gövdesi parça--parça daha sonra erişimi sağlar. Bu olarak adlandırılır *bir ileti okuma*.  
  
-   Bir bellek içi arabellek için kendi gövdesi de dahil olmak üzere tüm ileti kopyalanabilir <xref:System.ServiceModel.Channels.MessageBuffer> türü. Bu olarak adlandırılır *bir ileti kopyalama*.  
  
 Gövdesi erişebileceğiniz bir `Message` erişilme bağımsız olarak yalnızca bir kez,. İleti nesnesi olan bir `State` özelliği başlangıçta oluşturuldu olarak ayarlanır. Önceki listede açıklanan üç erişim yöntemlerine durumu yazılan, okuma ve kopyalanan, sırasıyla ayarlayın. Ayrıca, bir `Close` yöntemi ayarlayabilirsiniz durumunu Kapalı olarak iletinin gövde içeriği artık gerekli olduğunda. İleti gövdesi, yalnızca Created durumunda erişilebilir ve durumu değiştikten sonra oluşturulan duruma geri dönmek için bir yolu yoktur.  
  
## <a name="writing-messages"></a>İletiler  
 <xref:System.ServiceModel.Channels.Message.WriteBodyContents%28System.Xml.XmlDictionaryWriter%29> Yöntemi Yazar gövde içeriğini bir verilen `Message` örneği için belirli bir XML yazıcısı. <xref:System.ServiceModel.Channels.Message.WriteBody%2A> Yöntemi yapar, aynı şekilde, uygun kapsayıcı öğe içinde gövde içeriğini kapsayan dışında (örneğin, <`soap:body`>). Son olarak, <xref:System.ServiceModel.Channels.Message.WriteMessage%2A> kaydırma da dahil olmak üzere tüm ileti yazar SOAP zarfını ve üst bilgileri. SOAP kapatılırsa (<xref:System.ServiceModel.Channels.Message.Version> olan <xref:System.ServiceModel.Channels.MessageVersion.None?displayProperty=nameWithType>), her üç yöntemi aynı şeyi yapmak: Bunlar ileti gövdesi içeriği yazma.  
  
 Örneğin, bir dosyaya gelen ileti gövdesinin çıkış aşağıdaki kod yazar.  
  
 [!code-csharp[C_UsingTheMessageClass#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#5)]
 [!code-vb[C_UsingTheMessageClass#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#5)]  
  
 İki ek yardımcı yöntemler belirli SOAP başlangıç öğesi etiketleri yazın. Bu yöntemler, ileti gövdesi erişim sağlanır ve bunların kadar ileti durumu değişmez. Bu güncelleştirmeler şunlardır:  
  
-   <xref:System.ServiceModel.Channels.Message.WriteStartBody%2A> Örneğin, başlangıç body öğesi Yazar `<soap:Body>`.  
  
-   <xref:System.ServiceModel.Channels.Message.WriteStartEnvelope%2A> Örneğin, başlangıç Zarf öğesine Yazar `<soap:Envelope>`.  
  
 Karşılık gelen son öğe etiketlerini yazmak için çağrı `WriteEndElement` karşılık gelen XML yazıcısı. Bu yöntemleri doğrudan nadiren çağrılır.  
  
## <a name="reading-messages"></a>İletileri okuma  
 İleti gövdesini okumak için birincil yolu <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A>. Geri alma bir <xref:System.Xml.XmlDictionaryReader> ileti gövdesini okumak için kullanabilirsiniz. Unutmayın <xref:System.ServiceModel.Channels.Message> okuma durumu geçişleri hemen sonra <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> denir ve değil kullandığınızda döndürülen XML okuyucusu.  
  
 <xref:System.ServiceModel.Channels.Message.GetBody%2A> Yöntemi de ileti gövdesi olarak yazılmış bir nesne erişmesine olanak sağlar. Dahili olarak, bu yöntemde `GetReaderAtBodyContents`, ve ayrıca ileti durumuna geçiş <xref:System.ServiceModel.Channels.MessageState.Read> durumu (bkz <xref:System.ServiceModel.Channels.Message.State%2A> özelliği).  
  
 Denetlemek için iyi bir uygulamadır <xref:System.ServiceModel.Channels.Message.IsEmpty%2A> özelliği, içinde olduğu bu durum ileti gövdesi boş ve <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> oluşturur bir <xref:System.InvalidOperationException>. Bir alınan ileti (örneğin, yanıt) ise, ayrıca, siz de denetlemek isteyebilirsiniz <xref:System.ServiceModel.Channels.Message.IsFault%2A>, iletinin bir arıza içerip içermediğini belirtir.  
  
 En temel aşırı yüklemesini <xref:System.ServiceModel.Channels.Message.GetBody%2A> türü (genel parametre olarak belirtilir) kullanarak bir örneğine ileti gövdesi seri durumdan çıkarır bir <xref:System.Runtime.Serialization.DataContractSerializer> varsayılan ayarlarla ve yapılandırılmış <xref:System.Runtime.Serialization.DataContractSerializer.MaxItemsInObjectGraph%2A> kota devre dışı. Farklı serileştirme motoruna kullanın ya da yapılandırmak istiyorsanız `DataContractSerializer` varsayılan olmayan bir şekilde kullanma <xref:System.ServiceModel.Channels.Message.GetBody%2A> alan aşırı yüklemesini bir <xref:System.Runtime.Serialization.XmlObjectSerializer>.  
  
 Örneğin, aşağıdaki kod verileri seri hale getirilmiş bir içeren bir ileti gövdesi ayıklayan `Person` nesne ve kişinin adı yazdırır.  
  
 [!code-csharp[C_UsingTheMessageClass#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#6)]
 [!code-vb[C_UsingTheMessageClass#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#6)]  
  
## <a name="copying-a-message-into-a-buffer"></a>Bir iletiyi arabelleğe kopyalama  
 Bazen birden çok kez, ileti gövdesi örneğin erişmek için bir yayımcı abone sisteminin bir parçası olarak aynı iletiyi birden çok hedefe iletmek için gerekli değildir. Bu durumda, bellekte (gövde dahil) tüm ileti arabellek gereklidir. Bunu çağırarak yapmak <xref:System.ServiceModel.Channels.Message.CreateBufferedCopy%28System.Int32%29>. Bu yöntem, arabellek boyutu temsil eder ve bu boyuttan daha büyük bir arabellek oluşturur, bir tam sayı parametresi alır. İleti güvenilmeyen bir kaynaktan geliyorsa, bu güvenli bir değere ayarlamak önemlidir.  
  
 Arabellek olarak döndürülen bir <xref:System.ServiceModel.Channels.MessageBuffer> örneği. Çeşitli şekillerde arabellekteki verilere erişebilir. Çağırmak için birincil yoludur <xref:System.ServiceModel.Channels.Message.CreateMessage%2A> oluşturmak için `Message` arabellekteki örnekleri.  
  
 Arabellekteki verilere erişmek için başka bir şekilde uygulamaktır <xref:System.Xml.XPath.IXPathNavigable> arabirim <xref:System.ServiceModel.Channels.MessageBuffer> sınıfının temel alınan XML doğrudan erişmek için uygular. Bazı <xref:System.ServiceModel.Channels.MessageBuffer.CreateNavigator%2A> aşırı oluşturmanıza izin <xref:System.Xml.XPath> bir düğüm kota tarafından korunan gezginlerini ziyaret edilebilir XML düğüm sayısını sınırlama. Bu, uzun işleme zamana dayalı hizmet reddi saldırılarını önlemeye yardımcı olur. Bu teklif, varsayılan olarak devre dışıdır. Bazı `CreateNavigator` aşırı boşluk XML'de nasıl işlenmesi gerektiğini belirtmenize olanak tanır kullanarak <xref:System.Xml.XmlSpace> olan varsayılan ile numaralandırma `XmlSpace.None`.  
  
 İleti arabelleği içeriğine erişmek için bir son yolu kullanarak bir akış içeriğini çıkış yazmaktır <xref:System.ServiceModel.Channels.Message.WriteMessage%2A>.  
  
 Aşağıdaki örnek, birlikte çalışma işlemini gösterir. bir `MessageBuffer`: gelen ileti birden çok alıcıya iletilen ve ardından bir dosyaya oturum. İleti gövdesi yalnızca bir kez ardından erişilebilir olduğu arabelleğe alma olmadan bu mümkün değildir.  
  
 [!code-csharp[C_UsingTheMessageClass#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#7)]
 [!code-vb[C_UsingTheMessageClass#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#7)]  
  
 `MessageBuffer` Sınıfı önemli diğer üyelere sahiptir. <xref:System.ServiceModel.Channels.MessageBuffer.Close%2A> Yöntemi arabellek içeriği artık gerekli olduğunda kaynakları serbest bırakmak için çağrılabilir. <xref:System.ServiceModel.Channels.MessageBuffer.BufferSize%2A> Özelliği ayrılan arabelleğin boyutunu döndürür. <xref:System.ServiceModel.Channels.MessageBuffer.MessageContentType%2A> Özellik, iletinin MIME içerik türünü döndürür.  
  
## <a name="accessing-the-message-body-for-debugging"></a>Hata ayıklama ileti gövdesi erişme  
 Hata ayıklama amacıyla çağırabilirsiniz <xref:System.ServiceModel.Channels.Message.ToString%2A> iletinin gösterimini bir dize olarak almak için yöntemi. Bu gösterim, genellikle, metin Kodlayıcı ile kodlanmış, XML daha iyi okunabilirlik için biçimlendirilir dışında bir ileti kablo görüneceği şekilde eşleşir. Bunun tek istisnası, ileti gövdesi ' dir. Gövdesi yalnızca bir kez okuyabilir ve `ToString` ileti durumu değiştirmez. Bu nedenle, `ToString` yöntem gövdesi erişmek mümkün olmayabilir ve bir yer tutucu (örneğin, "..." yerine ya da üç nokta) yerine ileti gövdesi. Bu nedenle, kullanmayın `ToString` ileti gövdesi içeriğini önemliyse iletilerini günlüğe kaydetmek için.  
  
## <a name="accessing-other-message-parts"></a>Diğer ileti bölümlerini erişme  
 İleti gövdesi içeriğini dışında hakkında bilgilere erişmek için çeşitli özellikler sağlanır. Ancak, ileti kapatıldıktan sonra bu çağrılamaz:  
  
-   <xref:System.ServiceModel.Channels.Message.Headers%2A> Özelliğini ileti üstbilgilerini temsil eder. Bu konunun ilerleyen bölümlerindeki "Başlıklarında ile çalışma" bölümüne bakın.  
  
-   <xref:System.ServiceModel.Channels.Message.Properties%2A> Özelliğini iletiye eklenmiş adlandırılmış veri ileti gönderildiğinde genellikle yayılan değil parçalarıdır ileti özelliklerini temsil eder. Bu konunun ilerleyen bölümlerindeki "Özellikler ile çalışma" bölümüne bakın.  
  
-   <xref:System.ServiceModel.Channels.Message.Version%2A> Özelliği belirten iletiyle ilişkili SOAP ve WS-Addressing sürümü veya `None` SOAP devre dışı.  
  
-   <xref:System.ServiceModel.Channels.Message.IsFault%2A> Özelliği döndürür `true` ileti bir SOAP hatası iletisi ise.  
  
-   <xref:System.ServiceModel.Channels.Message.IsEmpty%2A> Özelliği döndürür `true` ileti boşsa.  
  
 Kullanabileceğiniz <xref:System.ServiceModel.Channels.Message.GetBodyAttribute%28System.String%2CSystem.String%29> gövdesi sarmalayıcı öğe üzerinde belirli bir özniteliği erişim yöntemi (örneğin, `<soap:Body>`) belirli bir ad ve ad alanı tarafından tanımlanan. Böyle bir öznitelik bulunamazsa `null` döndürülür. Bu yöntem yalnızca çağrılabilir `Message` (ileti gövdesi yok henüz eriştiğini olduğunda) Created durumunda olmadığı.  
  
## <a name="working-with-headers"></a>Üst bilgileri ile çalışma  
 A `Message` adlı adlandırılmış XML parçalarının herhangi bir sayıda içerebilir *üstbilgileri*. Her parça, normalde bir SOAP üst bilgisi için eşler. Üst bilgiler aracılığıyla erişilir `Headers` türünün özelliği <xref:System.ServiceModel.Channels.MessageHeaders>. <xref:System.ServiceModel.Channels.MessageHeaders> oluşan bir koleksiyondur <xref:System.ServiceModel.Channels.MessageHeaderInfo> üzerinden nesneleri ve ayrı üstbilgi erişilebilir kendi <xref:System.Collections.IEnumerable> arabirimi ya da kendi ındexer'dan. Örneğin, aşağıdaki kod tüm üst bilgilerinde adlarını listeler bir `Message`.  
  
 [!code-csharp[C_UsingTheMessageClass#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#8)]
 [!code-vb[C_UsingTheMessageClass#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#8)]  
  
#### <a name="adding-removing-finding-headers"></a>Ekleme, kaldırma, üst bilgileri bulma  
 Kullanarak tüm mevcut üst sonunda yeni üst bilgi ekleyebileceğiniz <xref:System.ServiceModel.Channels.MessageHeaders.Add%2A> yöntemi. Kullanabileceğiniz <xref:System.ServiceModel.Channels.MessageHeaders.Insert%2A> belirli bir dizinden bir başlık eklemek için yöntemi. Mevcut üst bilgileri için eklenen öğe kaydırılan. Üst bilgileri kendi dizini göre sıralanır ve ilk kullanılabilir dizini 0'dır. Çeşitli kullanabileceğiniz <xref:System.ServiceModel.Channels.MessageHeaders.CopyHeadersFrom%2A> farklı bir üst bilgilerini eklemek için yöntem aşırı yüklemeleri `Message` veya `MessageHeaders` örneği. Başkalarının tümünün kopyalarken bazı aşırı yüklemeler tek bir üstbilgi kopyalayın. <xref:System.ServiceModel.Channels.MessageHeaders.Clear%2A> Yöntemi, tüm üst bilgilerini kaldırır. <xref:System.ServiceModel.Channels.MessageHeaders.RemoveAt%2A> Yöntemi, bir üst bilgisi (tüm üstbilgileri sonra kaydırma) belirli bir dizinden kaldırır. <xref:System.ServiceModel.Channels.MessageHeaders.RemoveAll%2A> Yöntemi, belirli bir ad ve ad alanına sahip tüm başlıkları kaldırır.  
  
 Kullanarak bir özel üst bilgi alma <xref:System.ServiceModel.Channels.MessageHeaders.FindHeader%2A> yöntemi. Bu yöntem bulmak için üst bilgi ad alanı ve adını alır ve dizinini döndürür. Üst bilgi birden çok kez oluşursa bir özel durum oluşturulur. Üst bilgi bulunamadı -1 döndürür.  
  
 SOAP üstbilgisi modelinde, üst bilgiler olabilir bir `Actor` hedeflenen alıcı üst bilgisi belirten bir değer. En temel `FindHeader` aşırı yükleme yalnızca ileti için ultimate alıcı yönelik üst bilgileri arar. Başka bir aşırı ancak hangi belirtmenize olanak tanıyan `Actor` değerleri aramaya dahil edilir. Daha fazla bilgi için SOAP belirtimine bakın.  
  
 A <xref:System.ServiceModel.Channels.MessageHeaders.CopyTo%28System.ServiceModel.Channels.MessageHeaderInfo%5B%5D%2CSystem.Int32%29> yöntemi üst bilgiler kopyalamak için sağlanan bir <xref:System.ServiceModel.Channels.MessageHeaders> bir dizi koleksiyon <xref:System.ServiceModel.Channels.MessageHeaderInfo> nesneleri.  
  
 Bir üst bilgisindeki XML verilerine erişmek için çağırabilirsiniz <xref:System.ServiceModel.Channels.MessageHeaders.GetReaderAtHeader%2A> ve özel üstbilgi dizini için bir XML okuyucusu döndürür. Üst bilgi içeriği bir nesnede seri durumdan çıkarılacak istiyorsanız kullanın <xref:System.ServiceModel.Channels.MessageHeaders.GetHeader%60%601%28System.Int32%29> veya diğer aşırı yüklemeleri. En temel aşırı üst bilgileri kullanarak seri durumdan <xref:System.Runtime.Serialization.DataContractSerializer> yapılandırılmış varsayılan yolu. Farklı bir serileştirici veya farklı bir yapılandırma kullanmak istiyorsanız `DataContractSerializer`, aşırı birini bir `XmlObjectSerializer`. Üst bilgi adı, ad ve isteğe bağlı olarak bir listesini alan aşırı yükleme yapılmıştır `Actor` değerler yerine bir dizin; bu bir birleşimidir `FindHeader` ve `GetHeader`.  
  
## <a name="working-with-properties"></a>Özellikleriyle çalışma  
 A `Message` örnek, rastgele bir sayıdan rasgele türden adlandırılmış nesnelerin içerebilir. Bu koleksiyonu üzerinden erişilen `Properties` türünün özelliği `MessageProperties`. Koleksiyon uygular <xref:System.Collections.Generic.IDictionary%602> arabirim ve eşleme görevi gören <xref:System.String> için <xref:System.Object>. Normalde, özellik değerlerini doğrudan ileti herhangi bir bölümü için eşlemeyin, ancak bunun yerine çeşitli ileti işleme ipuçları WCF kanalı yığını veya çok çeşitli kanallara sağlar <xref:System.ServiceModel.Channels.MessageHeaders.CopyTo%28System.ServiceModel.Channels.MessageHeaderInfo%5B%5D%2CSystem.Int32%29> hizmet çerçevesi. Bir örnek için bkz. [aktarım veri mimarisine genel bakış](../../../../docs/framework/wcf/feature-details/data-transfer-architectural-overview.md).  
  
## <a name="inheriting-from-the-message-class"></a>İleti sınıfından devralma  
 Yerleşik türleri kullanılarak oluşturulan olursa `CreateMessage` değil gereksinimlerinizi karşılayacak, türetilen bir sınıf oluşturmanız `Message` sınıfı.  
  
### <a name="defining-the-message-body-contents"></a>İleti gövde içeriğini tanımlama  
 Üç birincil teknikleri mevcut bir ileti gövdesi içindeki verilere erişmek için: bir arabelleğe kopyalayarak yazma ve okuma. Bu işlemler, sonuçta neden <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%2A>, <xref:System.ServiceModel.Channels.Message.OnGetReaderAtBodyContents%2A>, ve <xref:System.ServiceModel.Channels.Message.OnCreateBufferedCopy%2A> , sırasıyla, türetilmiş sınıfınızın çağrılan yöntemler `Message`. Temel `Message` sınıfı garanti eder Bu yöntemlerden yalnızca biri her biri için çağrılır `Message` örneği ve onu birden çok kez çağrıldığını değil. Temel sınıf yöntemleri bir kapatılmış iletisinde çağırılır değil olduğunu da sağlar. Uygulamanızda ileti durumu izlemek için gerek yoktur.  
  
 <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%2A> bir soyut metottur ve uygulanmalıdır. İleti gövdesi içeriğini tanımlamanın en basit yolu, bu yöntemi kullanarak yazmaktır. Örneğin, aşağıdaki ileti 1 ila 20 100.000 rastgele sayılar içerir.  
  
 [!code-csharp[C_UsingTheMessageClass#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#9)]
 [!code-vb[C_UsingTheMessageClass#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#9)]  
  
 <xref:System.ServiceModel.Channels.Message.OnGetReaderAtBodyContents> Ve <xref:System.ServiceModel.Channels.Message.OnCreateBufferedCopy%2A> yöntemi çoğu durumda işe varsayılan uygulamaları vardır. Varsayılan uygulamaları çağrı <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%2A>, sonuçları arabelleğe ve elde edilen arabellek ile çalışabilirsiniz. Ancak, bazı durumlarda bu yeterli olmayabilir. Önceki örnekte, arzu olmayabilir arabelleğe alınan 100.000 XML öğeleri ileti sonuçları okunuyor. Geçersiz kılmak isteyebilirsiniz <xref:System.ServiceModel.Channels.Message.OnGetReaderAtBodyContents> özel döndürülecek <xref:System.Xml.XmlDictionaryReader> türetilmiş rastgele sayıları yukarı hizmet veren sınıf. Ardından kılabilirsiniz <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%2A> okuyucu kullanmak için <xref:System.ServiceModel.Channels.Message.OnGetReaderAtBodyContents> aşağıdaki örnekte gösterilen şekilde yöntemi döndürür.  
  
 [!code-csharp[C_UsingTheMessageClass#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#10)]
 [!code-vb[C_UsingTheMessageClass#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#10)]  
  
 Benzer şekilde, geçersiz kılmak isteyebilirsiniz `OnCreateBufferedCopy` kendi döndürülecek `MessageBuffer` türetilmiş sınıf.  
  
 İleti gövdesi içeriğini sağlamanın yanı sıra ileti türetilmiş sınıfınızın ayrıca kılmalı `Version`, `Headers`, ve `Properties` özellikleri.  
  
 Bir iletinin bir kopyasını oluşturma, kopyalama ait ileti üstbilgilerini orijinal kullandığına dikkat edin.  
  
### <a name="other-members-that-can-be-overridden"></a>Geçersiz kılınabilir diğer üyeleri  
 Geçersiz kılabilirsiniz <xref:System.ServiceModel.Channels.Message.OnWriteStartEnvelope%2A>, <xref:System.ServiceModel.Channels.Message.OnWriteStartHeaders%2A>, ve <xref:System.ServiceModel.Channels.Message.OnWriteStartBody%2A> yöntemleri nasıl SOAP Zarfı, SOAP üstbilgileri ve SOAP gövdesi öğe başlangıç etiketleri belirtmek için yazılır. Bu normalde karşılık `<soap:Envelope>`, `<soap:Header>`, ve `<soap:Body>`. Bu yöntemlerin herhangi bir şey IF yazmalısınız normalde <xref:System.ServiceModel.Channels.Message.Version> özelliği döndürür <xref:System.ServiceModel.Channels.MessageVersion.None>.  
  
> [!NOTE]
>  Varsayılan uygulaması `OnGetReaderAtBodyContents` çağrıları `OnWriteStartEnvelope` ve `OnWriteStartBody` çağırmadan önce `OnWriteBodyContents` ve sonuçları arabelleğe alma. Üstbilgileri dışarı değil.  
  
 Geçersiz kılma <xref:System.ServiceModel.Channels.Message.OnWriteMessage%2A> , yapıları tüm ileti yapılandırılmıştır şeklini değiştirmek için yöntemi. `OnWriteMessage` Yöntemi çağrılır <xref:System.ServiceModel.Channels.Message.WriteMessage%2A> ve varsayılan <xref:System.ServiceModel.Channels.Message.OnCreateBufferedCopy%2A> uygulaması. Bu geçersiz kılma Not <xref:System.ServiceModel.Channels.Message.WriteMessage%2A> en iyi yöntem değildir. Uygun geçersiz kılma daha iyidir `On` yöntemleri (örneğin, <xref:System.ServiceModel.Channels.Message.OnWriteStartEnvelope%2A>, <xref:System.ServiceModel.Channels.Message.OnWriteStartHeaders%2A>, ve <xref:System.ServiceModel.Channels.BodyWriter.OnWriteBodyContents%2A>.  
  
 Geçersiz kılma <xref:System.ServiceModel.Channels.Message.OnBodyToString%2A> , ileti gövdesi hata ayıklama sırasında nasıl temsil edildiğini geçersiz kılmak için. Üç nokta göstermek için ("...") varsayılandır. İleti durumu kapalı dışındaki herhangi bir şey olduğunda bu yöntem birden çok kez çağrılabilir dikkat edin. Bu yöntemin bir uygulaması, hiçbir zaman (örneğin, yalnızca iletme akışından okuma) yalnızca bir kez gerçekleştirilmesi gereken herhangi bir işlem neden olmaz.  
  
 Geçersiz kılma <xref:System.ServiceModel.Channels.Message.OnGetBodyAttribute%2A> SOAP gövdesi öğede öznitelikleri erişime izin vermek için yöntemi. Bu yöntem herhangi bir sayıda kez çağrılabilir ancak `Message` temel tür ileti Created durumunda olduğunda, yalnızca çağrıldığını güvence altına alır. Bir uygulamada durumunu denetlemek için gerekli değildir. Her zaman varsayılan uygulamasını döndürür `null`, body öğesi üzerinde hiçbir öznitelik olduğunu gösterir.  
  
 Varsa, `Message` ileti gövdesi artık gerekli olmadığında, nesne herhangi özel bir temizleme işlemi yapması gerekir, geçersiz kılabilirsiniz <xref:System.ServiceModel.Channels.Message.OnClose%2A>. Varsayılan uygulama, hiçbir şey yapmaz.  
  
 `IsEmpty` Ve `IsFault` özellikleri geçersiz kılınabilir. Varsayılan olarak, her ikisi de döndürür `false`.
