---
title: İleti Sınıfını Kullanma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d1d62bfb-2aa3-4170-b6f8-c93d3afdbbed
ms.openlocfilehash: 76ac5fad653604c7abe403def72d31696d26b547
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967841"
---
# <a name="using-the-message-class"></a>İleti Sınıfını Kullanma
<xref:System.ServiceModel.Channels.Message> Sınıfı Windows Communication Foundation (WCF) için temel bir sınıftır. İstemciler ve hizmetler arasındaki tüm iletişimler, sonuçta gönderilen <xref:System.ServiceModel.Channels.Message> ve alınan örneklerin sonucu olarak sonuçlanır.  
  
 Genellikle <xref:System.ServiceModel.Channels.Message> sınıfla doğrudan etkileşim kurmamalıdır. Bunun yerine, gelen ve giden iletileri anlatmak için veri sözleşmeleri, ileti sözleşmeleri ve işlem sözleşmeleri gibi WCF hizmet modeli yapıları kullanılır. Ancak, bazı Gelişmiş senaryolarda doğrudan <xref:System.ServiceModel.Channels.Message> sınıfını kullanarak program programlama yapabilirsiniz. Örneğin, <xref:System.ServiceModel.Channels.Message> sınıfını kullanmak isteyebilirsiniz:  
  
- Giden ileti içerikleri oluşturmak için alternatif bir yönteme ihtiyacınız olduğunda (örneğin, diskteki bir dosyadan doğrudan bir ileti oluşturma) .NET Framework nesneleri serileştirmek yerine.  
  
- Gelen ileti içeriklerini (örneğin, Ham XML içeriklerine XSLT dönüştürmesi uygulamak istediğinizde) .NET Framework nesneleri içine çıkarmak yerine farklı bir şekilde kullanmanız gerektiğinde.  
  
- İletileri ileti içeriğinden bağımsız olarak genel bir şekilde (örneğin, yönlendirici oluştururken veya iletme, yük dengeleyici ya da bir yayımlama-abonelik sistemi) kullanmanız gerektiğinde.  
  
 <xref:System.ServiceModel.Channels.Message> Sınıfını kullanmadan önce [veri aktarımı mimarisine genel bakış](../../../../docs/framework/wcf/feature-details/data-transfer-architectural-overview.md)' da WCF veri aktarımı mimarisini öğrenin.  
  
 <xref:System.ServiceModel.Channels.Message> , Veriler için genel amaçlı bir kapsayıcıdır, ancak tasarımı SOAP protokolünde bir iletinin tasarımını yakından izler. SOAP içinde olduğu gibi, bir iletinin hem ileti gövdesi hem de üst bilgileri vardır. İleti gövdesinde gerçek yük verileri bulunur, ancak üstbilgiler adlandırılmış veri kapsayıcıları içerir. Gövde ve üst bilgileri okuma ve yazma kuralları farklıdır; Örneğin, üst bilgilerin her zaman bellekte ara belleğe alınır ve gövde yalnızca bir kez okunabilir ve akış yapılabilir olabilir. Normal olarak, SOAP kullanırken ileti gövdesi SOAP gövdesine eşlenir ve ileti başlıkları SOAP üst bilgilerine eşlenir.  
  
## <a name="using-the-message-class-in-operations"></a>Işlemlerde Ileti sınıfını kullanma  
 <xref:System.ServiceModel.Channels.Message> Sınıfını bir işlemin giriş parametresi, bir işlemin dönüş değeri veya her ikisi de kullanabilirsiniz. <xref:System.ServiceModel.Channels.Message> Bir işlemde herhangi bir yerde kullanılırsa, aşağıdaki kısıtlamalar geçerlidir:  
  
- İşlem herhangi bir `out` veya `ref` parametreye sahip olamaz.  
  
- Birden fazla `input` parametre olamaz. Parametresi varsa, ya Ileti ya da bir ileti sözleşmesi türü olmalıdır.  
  
- Dönüş türü `void`, `Message`ya da bir ileti sözleşmesi türü olmalıdır.  
  
 Aşağıdaki kod örneği geçerli bir işlem sözleşmesi içerir.  
  
 [!code-csharp[C_UsingTheMessageClass#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#1)]
 [!code-vb[C_UsingTheMessageClass#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#1)]  
  
## <a name="creating-basic-messages"></a>Temel Iletileri oluşturma  
 Sınıfı <xref:System.ServiceModel.Channels.Message> , temel iletileri `CreateMessage` oluşturmak için kullanabileceğiniz statik fabrika yöntemleri sağlar.  
  
 Tüm `CreateMessage` aşırı yüklemeler, ileti için kullanılacak soap <xref:System.ServiceModel.Channels.MessageVersion> ve ws-Addressing sürümlerini gösteren türünde bir sürüm parametresi alır. Gelen iletiyle aynı protokol sürümlerini kullanmak istiyorsanız, <xref:System.ServiceModel.OperationContext.IncomingMessageVersion%2A> <xref:System.ServiceModel.OperationContext.Current%2A> özelliğinden elde edilen <xref:System.ServiceModel.OperationContext> örnekteki özelliğini kullanabilirsiniz. Çoğu `CreateMessage` aşırı yüklemenin Ayrıca ileti için kullanılacak soap eylemini gösteren bir dize parametresi vardır. Sürüm, soap Zarfı oluşturmayı `None` devre dışı bırakmak için olarak ayarlanabilir; ileti yalnızca gövdeden oluşur.  
  
## <a name="creating-messages-from-objects"></a>Nesnelerden Ileti oluşturma  
 Yalnızca bir sürümü `CreateMessage` alan en temel aşırı yükleme ve bir eylem, boş bir gövdeye sahip bir ileti oluşturur. Başka bir aşırı yükleme ek <xref:System.Object> bir parametre alır; bu, gövdesi verilen nesnenin serileştirilmiş temsili olan bir ileti oluşturur. <xref:System.Runtime.Serialization.DataContractSerializer> Serileştirme için varsayılan ayarlarla kullanın. Farklı bir serileştirici kullanmak istiyorsanız ya `DataContractSerializer` da farklı şekilde yapılandırmak istiyorsanız, aynı zamanda bir `XmlObjectSerializer` parametre alan `CreateMessage` aşırı yüklemeyi kullanın.  
  
 Örneğin, bir iletiye bir nesne döndürmek için aşağıdaki kodu kullanabilirsiniz.  
  
 [!code-csharp[C_UsingTheMessageClass#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#2)]
 [!code-vb[C_UsingTheMessageClass#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#2)]  
  
## <a name="creating-messages-from-xml-readers"></a>XML okuyucularından Ileti oluşturma  
 Bir nesne yerine gövde <xref:System.Xml.XmlDictionaryReader> için bir <xref:System.Xml.XmlReader> veya olan aşırıyüklemelervardır.`CreateMessage` Bu durumda, iletinin gövdesi, geçirilen XML okuyucusundan okunmadan elde edilen XML 'yi içerir. Örneğin, aşağıdaki kod, gövde içeriği bir XML dosyasından okunan bir ileti döndürür.  
  
 [!code-csharp[C_UsingTheMessageClass#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#3)]
 [!code-vb[C_UsingTheMessageClass#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#3)]  
  
 Buna ek olarak, `CreateMessage` yalnızca gövde değil, <xref:System.Xml.XmlReader> tüm iletiyi <xref:System.Xml.XmlDictionaryReader> temsil eden veya içeren aşırı yüklemeler vardır. Bu aşırı yüklemeler Ayrıca bir tamsayı `maxSizeOfHeaders` parametresi alır. Üst bilgiler, ileti oluşturulduğu anda her zaman bellek olarak arabelleğe alınır ve bu parametre, gerçekleşen arabelleğe alma miktarını sınırlandırır. Bir hizmet reddi saldırısı olasılığını azaltmak için, XML güvenilmeyen bir kaynaktan geliyorsa bu parametrenin güvenli bir değere ayarlanması önemlidir. XML okuyucusunun temsil ettiği iletinin SOAP ve WS-Addressing sürümleri, sürüm parametresi kullanılarak belirtilen sürümlerle eşleşmelidir.  
  
## <a name="creating-messages-with-bodywriter"></a>BodyWriter ile Ileti oluşturma  
 Bir `CreateMessage` aşırı yükleme, `BodyWriter` iletinin gövdesini tanımlayacak bir örnek alır. `BodyWriter` , İleti gövdelerinin nasıl oluşturulduğunu özelleştirmek için türetilebilen soyut bir sınıftır. İleti gövdelerini özel bir şekilde `BodyWriter` anlatmak için kendi türetilmiş sınıfınızı oluşturabilirsiniz. Alan yöntemini`BodyWriter.OnWriteBodyContents` geçersiz kılmanız gerekir ;Buyöntem,gövdeyiyazmadansorumludur.<xref:System.Xml.XmlDictionaryWriter>  
  
 Gövde yazıcılarının ara belleğe alınabilir veya ara belleğe alınmamış (akış). Arabelleğe alınmış gövde yazarları içerikleri herhangi bir sayıda yazabilir, ancak akışa alma içerikleri yalnızca bir kez yazılabilir. Özelliği `IsBuffered` , gövde yazıcısının arabelleğe alınıp alınmayacağını gösterir. Bu değeri, bir `BodyWriter` `isBuffered` Boolean parametresi alan korumalı oluşturucuyu çağırarak gövde yazıcınız için ayarlayabilirsiniz. Gövde yazarları, arabelleğe alınmamış bir gövde yazıcısından arabellekli bir gövde yazıcısının oluşturulmasını destekler. Bu işlemi özelleştirmek için `OnCreateBufferedCopy` yöntemini geçersiz kılabilirsiniz. Varsayılan olarak, tarafından `OnWriteBodyContents` döndürülen xml içeren bir bellek içi arabellek kullanılır. `OnCreateBufferedCopy`bir `maxBufferSize` tamsayı parametresi alır; bu yöntemi geçersiz kılarsınız, bu en büyük boyuttan daha büyük arabellekler oluşturmamalıdır.  
  
 `WriteBodyContents` Sınıfı,`CreateBufferedCopy` sırasıyla ve`OnWriteBodyContents` yöntemleri etrafında ölçülü sarmalayıcılar olan ve yöntemlerini sağlar. `OnCreateBufferedCopy` `BodyWriter` Bu yöntemler, arabelleğe alınmamış bir gövde yazıcısında birden çok kez erişilmediğinden emin olmak için durum denetimi gerçekleştirir. Bu yöntemler doğrudan yalnızca öğesine `Message` `BodyWriters`dayalı özel türetilmiş sınıflar oluşturulurken çağrılır.  
  
## <a name="creating-fault-messages"></a>Hata Iletileri oluşturma  
 SOAP hata iletileri oluşturmak `CreateMessage` için belirli aşırı yüklemeleri kullanabilirsiniz. Bunların en temel, hatayı açıklayan bir <xref:System.ServiceModel.Channels.MessageFault> nesne alır. Kolaylık sağlamak için diğer aşırı yüklemeler sunulmaktadır. İlk bu aşırı yükleme bir `FaultCode` ve neden dizesi alır ve bu bilgileri kullanarak bir `MessageFault.CreateFault` `MessageFault` kullanarak oluşturur. Diğer aşırı yükleme bir ayrıntı nesnesi alır ve ayrıca hata kodu ve `CreateFault` nedeni ile birlikte bir araya geçirir. Örneğin, aşağıdaki işlem bir hata döndürür.  
  
 [!code-csharp[C_UsingTheMessageClass#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#4)]
 [!code-vb[C_UsingTheMessageClass#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#4)]  
  
## <a name="extracting-message-body-data"></a>Ileti gövdesi verileri ayıklanıyor  
 Sınıfı `Message` , gövdeden bilgi ayıklamanın birden çok yolunu destekler. Bunlar aşağıdaki kategorilerde sınıflandırılabilir:  
  
- Tüm ileti gövdesinin bir kez bir XML yazıcı olarak yazılmış şekilde alınması. Bu, *ileti yazma*olarak adlandırılır.  
  
- İleti gövdesi üzerinde bir XML okuyucusu alma. Bu, daha sonra ileti gövdesine gereken şekilde parça erişimini sağlamanıza olanak sağlar. Bu, *ileti okuma*olarak adlandırılır.  
  
- Gövdesi dahil olmak üzere tüm ileti, <xref:System.ServiceModel.Channels.MessageBuffer> türün bellek içi arabelleğine kopyalanabilir. Buna *bir ileti kopyalama*denir.  
  
 Ne olursa olsun, bir yalnızca bir `Message` kez gövdeye erişebilirsiniz. Bir ileti nesnesi, başlangıçta `State` oluşturulması için ayarlanmış olan bir özelliğine sahiptir. Yukarıdaki listede açıklanan üç erişim yöntemi, sırasıyla durum yazılır, okundu ve kopyalanabilir olarak ayarlanır. Ayrıca, ileti `Close` gövdesi içerikleri artık gerekli olmadığında bir yöntem durumu kapalı olarak ayarlayabilir. İleti gövdesine yalnızca oluşturulan durumda erişilebilir ve durum değiştirildikten sonra oluşturulan duruma geri dönmenin bir yolu yoktur.  
  
## <a name="writing-messages"></a>Ileti yazma  
 <xref:System.ServiceModel.Channels.Message.WriteBodyContents%28System.Xml.XmlDictionaryWriter%29> Yöntemi belirli`Message` bir örneğin gövde içeriğini belirli bir XML yazıcısına yazar. Yöntemi, gövde içeriğini uygun sarmalayıcı öğesine (örneğin, <`soap:body`>) içermedikçe aynı şekilde yapar. <xref:System.ServiceModel.Channels.Message.WriteBody%2A> Son olarak, sarmalama soap Zarfı ve üst bilgileri de dahil olmak üzere tüm iletiyi yazar.<xref:System.ServiceModel.Channels.Message.WriteMessage%2A> SOAP kapalıysa (<xref:System.ServiceModel.Channels.Message.Version> ise <xref:System.ServiceModel.Channels.MessageVersion.None?displayProperty=nameWithType>), üç yöntem de aynı şeyi yapar: ileti gövdesi içeriklerini yazar.  
  
 Örneğin, aşağıdaki kod, gelen bir iletinin gövdesini bir dosyaya yazar.  
  
 [!code-csharp[C_UsingTheMessageClass#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#5)]
 [!code-vb[C_UsingTheMessageClass#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#5)]  
  
 İki ek yardımcı yöntem, belirli SOAP başlangıç öğesi etiketlerini yazar. Bu yöntemler ileti gövdesine erişemez ve bu nedenle ileti durumunu değiştirmez. Bu güncelleştirmeler şunlardır:  
  
- <xref:System.ServiceModel.Channels.Message.WriteStartBody%2A>başlangıç gövdesi öğesini (örneğin, `<soap:Body>`) yazar.  
  
- <xref:System.ServiceModel.Channels.Message.WriteStartEnvelope%2A>başlangıç zarfı öğesini (örneğin, `<soap:Envelope>`) yazar.  
  
 Karşılık gelen bitiş öğesi etiketlerini yazmak için ilgili XML `WriteEndElement` yazıcı üzerinde öğesini çağırın. Bu yöntemler nadiren doğrudan çağırılır.  
  
## <a name="reading-messages"></a>Iletileri okuma  
 Bir ileti gövdesini okumayı sağlamanın birincil yolu, çağrıladır <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A>. İleti gövdesini okumak için <xref:System.Xml.XmlDictionaryReader> kullanabileceğiniz bir geri alırsınız. Döndürülen XML okuyucusunu kullandığınızda değil, okuma durumuna <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> yapılan geçişlerinçağrılır.<xref:System.ServiceModel.Channels.Message>  
  
 <xref:System.ServiceModel.Channels.Message.GetBody%2A> Yöntemi, ileti gövdesine türü belirlenmiş bir nesne olarak erişmenizi de sağlar. Dahili olarak, bu yöntem `GetReaderAtBodyContents`kullanır ve ayrıca ileti durumunu <xref:System.ServiceModel.Channels.MessageState.Read> duruma geçirir (bkz <xref:System.ServiceModel.Channels.Message.State%2A> . özelliği).  
  
 <xref:System.ServiceModel.Channels.Message.IsEmpty%2A> Özelliğini denetlemek iyi bir uygulamadır, bu durumda ileti gövdesi boştur ve <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> bir <xref:System.InvalidOperationException>oluşturur. Ayrıca, alınan bir iletidir (örneğin, yanıt), iletinin bir hata içerip içermediğini belirten denetlemek <xref:System.ServiceModel.Channels.Message.IsFault%2A>de isteyebilirsiniz.  
  
 ' Nin <xref:System.ServiceModel.Channels.Message.GetBody%2A> en temel aşırı yüklemesi, <xref:System.Runtime.Serialization.DataContractSerializer.MaxItemsInObjectGraph%2A> varsayılan ayarlarla yapılandırılmış ve kotasının devre dışı bırakıldığı bir <xref:System.Runtime.Serialization.DataContractSerializer> tür örneğine (genel parametresiyle belirtilir) ileti gövdesini serileştirir. Farklı bir serileştirme altyapısı kullanmak veya varsayılan olmayan bir şekilde yapılandırmak `DataContractSerializer` istiyorsanız, alan <xref:System.ServiceModel.Channels.Message.GetBody%2A> <xref:System.Runtime.Serialization.XmlObjectSerializer>Aşırı yüklemeyi kullanın.  
  
 Örneğin, aşağıdaki kod serileştirilmiş `Person` bir nesne içeren bir ileti gövdesinden verileri ayıklar ve kişinin adını yazdırır.  
  
 [!code-csharp[C_UsingTheMessageClass#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#6)]
 [!code-vb[C_UsingTheMessageClass#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#6)]  
  
## <a name="copying-a-message-into-a-buffer"></a>Bir Iletiyi arabelleğe kopyalama  
 Bazen ileti gövdesine birden çok kez erişmek gerekir, örneğin, aynı iletiyi Yayımcı-abone sisteminin bir parçası olarak birden fazla hedefe iletmek için. Bu durumda, bellekteki tüm iletiyi (gövde dahil) arabelleğe almak gereklidir. Bunu çağırarak <xref:System.ServiceModel.Channels.Message.CreateBufferedCopy%28System.Int32%29>yapabilirsiniz. Bu yöntem, en büyük arabellek boyutunu temsil eden bir tamsayı parametresi alır ve bu boyuttan daha büyük olmayan bir arabellek oluşturur. İleti güvenilmeyen bir kaynaktan geliyorsa bunu güvenli bir değere ayarlamanız önemlidir.  
  
 Arabellek bir <xref:System.ServiceModel.Channels.MessageBuffer> örnek olarak döndürülür. Arabellekteki verilere çeşitli yollarla erişebilirsiniz. Birincil yol, arabellekteki örnekleri oluşturmak <xref:System.ServiceModel.Channels.Message.CreateMessage%2A> `Message` için çağrıladır.  
  
 Arabellekteki verilere erişmenin başka bir yolu, <xref:System.Xml.XPath.IXPathNavigable> <xref:System.ServiceModel.Channels.MessageBuffer> sınıfın temel alınan XML 'e doğrudan erişmek için uyguladığı arabirimi uygulamaktır. Bazı <xref:System.ServiceModel.Channels.MessageBuffer.CreateNavigator%2A> aşırı yüklemeler, bir düğüm <xref:System.Xml.XPath> kotasıyla korunan ve ziyaret edilecek XML düğümlerinin sayısını sınırlayan gezintiler oluşturmanızı sağlar. Bu, uzun işlem süresine göre hizmet reddi saldırılarını önlemeye yardımcı olur. Bu teklif varsayılan olarak devre dışıdır. Bazı `CreateNavigator` aşırı <xref:System.Xml.XmlSpace> yüklemeler`XmlSpace.None`, varsayılan değer olarak, sabit listesini kullanarak XML 'de ne kadar boşluk işleneceğini belirtmenizi sağlar.  
  
 İleti arabelleğinin içeriğine erişmenin son bir yolu, kullanarak <xref:System.ServiceModel.Channels.Message.WriteMessage%2A>içeriğini bir akışa yazmaktır.  
  
 Aşağıdaki örnek, ile `MessageBuffer`çalışma sürecini gösterir: gelen bir ileti birden çok alıcıya iletilir ve sonra bir dosyaya kaydedilir. Arabelleğe alma olmadan bu mümkün değildir, çünkü ileti gövdesine yalnızca bir kez erişilebilir.  
  
 [!code-csharp[C_UsingTheMessageClass#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#7)]
 [!code-vb[C_UsingTheMessageClass#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#7)]  
  
 Sınıfı `MessageBuffer` , başka üyelere dikkat edin. Bu <xref:System.ServiceModel.Channels.MessageBuffer.Close%2A> Yöntem, arabellek içerikleri artık gerekli olmadığında kaynakları serbest bırakmak için çağrılabilir. Özelliği <xref:System.ServiceModel.Channels.MessageBuffer.BufferSize%2A> , ayrılan arabelleğin boyutunu döndürür. <xref:System.ServiceModel.Channels.MessageBuffer.MessageContentType%2A> Özelliği iletinin MIME içerik türünü döndürür.  
  
## <a name="accessing-the-message-body-for-debugging"></a>Hata ayıklama için Ileti gövdesine erişme  
 Hata ayıklama amacıyla, bir dize olarak iletinin <xref:System.ServiceModel.Channels.Message.ToString%2A> gösterimini almak için yöntemini çağırabilirsiniz. Bu gösterim genellikle, metin kodlayıcıyla kodlanmışsa, XML 'in insanlar okunabilirlik için daha iyi biçimlendirildiğinden emin olmak dışında, bir iletinin bir ileti ile kodlanması ile aynı şekilde ele alınmasıdır. Bunun tek istisnası ileti gövdesidir. Gövde yalnızca bir kez okunabilir ve `ToString` ileti durumunu değiştirmez. Bu nedenle, `ToString` Yöntem gövdeye erişebilmeyebilir ve bir yer tutucuyu (örneğin, "...") kullanabilir. ya da üç nokta) ileti gövdesi yerine. Bu nedenle, iletilerin gövde `ToString` içeriği önemliyse iletileri günlüğe kaydetmek için kullanmayın.  
  
## <a name="accessing-other-message-parts"></a>Diğer Ileti bölümlerine erişme  
 Gövde içerikleri dışındaki iletiyle ilgili bilgilere erişmek için çeşitli özellikler sağlanır. Ancak, ileti kapatıldıktan sonra bunlar çağrılamaz:  
  
- <xref:System.ServiceModel.Channels.Message.Headers%2A> Özelliği ileti üstbilgilerini temsil eder. Bu konunun ilerleyen kısımlarında yer alan "üstbilgileriyle çalışma" bölümüne bakın.  
  
- <xref:System.ServiceModel.Channels.Message.Properties%2A> Özelliği, ileti gönderildiğinde genellikle yayınlanmayan iletiye eklenen adlandırılmış veri parçaları olan ileti özelliklerini temsil eder. Bu konunun ilerleyen kısımlarında yer alan "özelliklerle çalışma" bölümüne bakın.  
  
- Özelliği, iletiyle ilişkili soap ve ws-Addressing sürümünü, ya `None` da SOAP devre dışı olduğunu gösterir. <xref:System.ServiceModel.Channels.Message.Version%2A>  
  
- Özelliği, ileti bir SOAP hata iletisi ise döndürür `true`. <xref:System.ServiceModel.Channels.Message.IsFault%2A>  
  
- Özelliği, ileti `true` boşsa döndürür. <xref:System.ServiceModel.Channels.Message.IsEmpty%2A>  
  
 Belirli bir ad ve <xref:System.ServiceModel.Channels.Message.GetBodyAttribute%28System.String%2CSystem.String%29> ad alanı tarafından tanımlanan gövde sarmalayıcı öğesi (örneğin, `<soap:Body>`) üzerinde belirli bir özniteliğe erişmek için yöntemini kullanabilirsiniz. Böyle bir öznitelik bulunamazsa, `null` döndürülür. Bu yöntem yalnızca `Message` oluşturma durumunda olduğunda çağrılabilir (ileti gövdesine henüz erişilmemişse).  
  
## <a name="working-with-headers"></a>Üstbilgileriyle çalışma  
 , `Message` *Üst bilgiler*olarak adlandırılan herhangi bir sayıda adlandırılmış XML parçacığı içerebilir. Her parça normalde bir SOAP üstbilgisiyle eşlenir. Üst bilgilere, `Headers` türünün <xref:System.ServiceModel.Channels.MessageHeaders>özelliği aracılığıyla erişilir. <xref:System.ServiceModel.Channels.MessageHeaders>bir <xref:System.ServiceModel.Channels.MessageHeaderInfo> nesne koleksiyonudur ve tek bir üst bilgiye kendi <xref:System.Collections.IEnumerable> arabiriminden ya da onun Dizin Oluşturucusu aracılığıyla erişilebilir. Örneğin, aşağıdaki kod, içindeki `Message`tüm üstbilgilerin adlarını listeler.  
  
 [!code-csharp[C_UsingTheMessageClass#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#8)]
 [!code-vb[C_UsingTheMessageClass#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#8)]  
  
#### <a name="adding-removing-finding-headers"></a>Üst bilgileri ekleme, kaldırma, bulma  
 <xref:System.ServiceModel.Channels.MessageHeaders.Add%2A> Yöntemini kullanarak tüm mevcut üstbilgilerin sonuna yeni bir üst bilgi ekleyebilirsiniz. Belirli bir dizine üst <xref:System.ServiceModel.Channels.MessageHeaders.Insert%2A> bilgi eklemek için yöntemini kullanabilirsiniz. Eklenen öğe için mevcut üstbilgiler kaydırılacağı. Üst bilgiler, dizinlerine göre sıralanır ve kullanılabilir ilk dizin 0 ' dır. Farklı <xref:System.ServiceModel.Channels.MessageHeaders.CopyHeadersFrom%2A> bir`Message` veya örneğindenüstbilgieklemekiçinçeşitli`MessageHeaders` Yöntem yüklerini kullanabilirsiniz. Bazı aşırı yüklemeler tek bir üst bilgiyi kopyalar, diğerleri ise tümünü kopyalar. <xref:System.ServiceModel.Channels.MessageHeaders.Clear%2A> Yöntemi tüm üst bilgileri kaldırır. <xref:System.ServiceModel.Channels.MessageHeaders.RemoveAt%2A> Yöntemi belirli bir dizindeki bir üst bilgiyi kaldırır (sonrasında tüm üst bilgileri kaydırma). Yöntemi <xref:System.ServiceModel.Channels.MessageHeaders.RemoveAll%2A> , belirli bir ad ve ad alanı ile tüm üstbilgileri kaldırır.  
  
 <xref:System.ServiceModel.Channels.MessageHeaders.FindHeader%2A> Yöntemini kullanarak belirli bir üst bilgiyi alın. Bu yöntem, bulunacak üstbilginin adını ve ad alanını alır ve dizinini döndürür. Üst bilgi birden çok kez oluşursa, bir özel durum oluşturulur. Üst bilgi bulunamazsa,-1 döndürür.  
  
 SOAP üstbilgi modelinde, üst bilgilerin amaçlanan alıcıyı belirten bir `Actor` değeri olabilir. En temel `FindHeader` aşırı yükleme yalnızca iletinin son alıcısı için tasarlanan üstbilgileri arar. Ancak, başka bir aşırı yükleme, aramaya hangi `Actor` değerlerin ekleneceğini belirtmenize olanak sağlar. Daha fazla bilgi için bkz. SOAP belirtimi.  
  
 Bir <xref:System.ServiceModel.Channels.MessageHeaders.CopyTo%28System.ServiceModel.Channels.MessageHeaderInfo%5B%5D%2CSystem.Int32%29> koleksiyondakiüst<xref:System.ServiceModel.Channels.MessageHeaders> bilgileri bir nesnedizisinekopyalamakiçinbiryöntemsağlanır.<xref:System.ServiceModel.Channels.MessageHeaderInfo>  
  
 Bir başlıktaki XML verilerine erişmek için, belirli bir üst bilgi dizini <xref:System.ServiceModel.Channels.MessageHeaders.GetReaderAtHeader%2A> için bir XML okuyucusu çağırabilir ve döndürebilirsiniz. Üst bilgi içeriğini bir nesne veya diğer aşırı yüklerden birini kullanarak <xref:System.ServiceModel.Channels.MessageHeaders.GetHeader%60%601%28System.Int32%29> seri durumdan çıkarmak istiyorsanız. En temel aşırı yüklemeler varsayılan şekilde <xref:System.Runtime.Serialization.DataContractSerializer> yapılandırılmış kullanılarak üst bilgilerin serisini kaldıramıyor. Farklı bir serileştirici veya farklı bir yapılandırması `DataContractSerializer`kullanmak istiyorsanız, bir `XmlObjectSerializer`kullanan aşırı yüklemelerin birini kullanın. Ayrıca üst bilgi adını, ad alanını ve isteğe bağlı olarak bir dizin yerine bir `Actor` değer listesini alan aşırı yüklemeler de vardır; bu bir `FindHeader` ve `GetHeader`birleşimidir.  
  
## <a name="working-with-properties"></a>Özelliklerle çalışma  
 Bir `Message` örnek rastgele türlerde adlandırılmış nesneleri rastgele bir dizi içerebilir. Bu koleksiyona, `Properties` türünün `MessageProperties`özelliği aracılığıyla erişilir. Koleksiyon <xref:System.Collections.Generic.IDictionary%602> arabirimini uygular ve öğesinden <xref:System.String> öğesine <xref:System.Object>eşleme görevi görür. Normalde, özellik değerleri doğrudan iletinin herhangi bir bölümüne doğrudan eşlenmiyor, ancak WCF kanal yığınındaki veya <xref:System.ServiceModel.Channels.MessageHeaders.CopyTo%28System.ServiceModel.Channels.MessageHeaderInfo%5B%5D%2CSystem.Int32%29> hizmet çerçevesindeki çeşitli kanallara çeşitli ileti işleme ipuçları sağlar. Bir örnek için bkz. [veri aktarımı mimari genel bakış](../../../../docs/framework/wcf/feature-details/data-transfer-architectural-overview.md).  
  
## <a name="inheriting-from-the-message-class"></a>Ileti sınıfından devralma  
 Kullanılarak `CreateMessage` oluşturulan yerleşik ileti türleri gereksinimlerinizi karşılamıyorsa, `Message` sınıfından türetilen bir sınıf oluşturun.  
  
### <a name="defining-the-message-body-contents"></a>Ileti gövdesi Içeriğini tanımlama  
 İleti gövdesinde verilere erişmek için üç birincil teknik mevcuttur: bir arabelleğe yazma, okuma ve bu verileri kopyalama. Bu işlemler, sonunda, ve <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%2A>' <xref:System.ServiceModel.Channels.Message.OnGetReaderAtBodyContents%2A>ın `Message`türetilmiş <xref:System.ServiceModel.Channels.Message.OnCreateBufferedCopy%2A> sınıfınıza sırasıyla,, ve yöntemlerinin çağrılmakta olduğunu sonuç olarak sonuçlanır. Temel `Message` sınıf, her `Message` örnek için yalnızca bir tane Bu yöntemden bir kez çağrıldığına ve bir kereden fazla çağrılmadığından emin olur. Temel sınıf Ayrıca yöntemlerin kapalı bir ileti üzerinde çağrılmamasını sağlar. Uygulamanızda ileti durumunun izlenmesi gerekmez.  
  
 <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%2A>soyut bir yöntemdir ve uygulanması gerekir. İletinizin gövde içeriğini tanımlamanın en temel yolu bu yöntemi kullanarak yazmalıdır. Örneğin, aşağıdaki ileti 1 ile 20 arasında 100.000 rastgele sayı içerir.  
  
 [!code-csharp[C_UsingTheMessageClass#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#9)]
 [!code-vb[C_UsingTheMessageClass#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#9)]  
  
 <xref:System.ServiceModel.Channels.Message.OnGetReaderAtBodyContents> Ve<xref:System.ServiceModel.Channels.Message.OnCreateBufferedCopy%2A> yöntemlerinin çoğu durumda çalışan varsayılan uygulamaları vardır. Varsayılan uygulamalar çağrı <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%2A>yapın, sonuçları arabelleğe alarak elde edilen arabellekten çalışır. Ancak, bazı durumlarda bu yeterli olmayabilir. Yukarıdaki örnekte, iletiyi okumak 100.000 XML öğelerinin arabelleğe alındığı, bu da istenmeyebilir. Rastgele sayılar sunan özel <xref:System.ServiceModel.Channels.Message.OnGetReaderAtBodyContents> <xref:System.Xml.XmlDictionaryReader> bir türetilmiş sınıf döndürmek için geçersiz kılmak isteyebilirsiniz. Ardından, aşağıdaki örnekte <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%2A> gösterildiği gibi, <xref:System.ServiceModel.Channels.Message.OnGetReaderAtBodyContents> yöntemin döndürdüğü okuyucuyu kullanmak için geçersiz kılabilirsiniz.  
  
 [!code-csharp[C_UsingTheMessageClass#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#10)]
 [!code-vb[C_UsingTheMessageClass#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#10)]  
  
 Benzer şekilde, kendi `OnCreateBufferedCopy` `MessageBuffer` türetilmiş sınıfınızı döndürmek için geçersiz kılmak isteyebilirsiniz.  
  
 İleti gövdesi içerikleri sağlamaya ek olarak, iletiniz türetilmiş sınıfınız `Version`, `Headers`, ve `Properties` özelliklerini de geçersiz kılmalıdır.  
  
 İletinin bir kopyasını oluşturursanız, kopyanın başlangıçtaki ileti üstbilgilerini kullandığını unutmayın.  
  
### <a name="other-members-that-can-be-overridden"></a>Geçersiz kılınabilen diğer Üyeler  
 Soap Zarfı, SOAP <xref:System.ServiceModel.Channels.Message.OnWriteStartEnvelope%2A>üstbilgileri <xref:System.ServiceModel.Channels.Message.OnWriteStartHeaders%2A>ve SOAP gövdesi öğe başlangıç etiketlerinin nasıl yazıldığını belirtmek için, ve <xref:System.ServiceModel.Channels.Message.OnWriteStartBody%2A> yöntemlerini geçersiz kılabilirsiniz. Bunlar normalde `<soap:Envelope>`, `<soap:Header>`ve `<soap:Body>`' a karşılık gelir. Bu yöntemler normalde, <xref:System.ServiceModel.Channels.Message.Version> özelliği döndürürse <xref:System.ServiceModel.Channels.MessageVersion.None>bir şeyi yazmamalıdır.  
  
> [!NOTE]
> `OnGetReaderAtBodyContents` Çağrılarıçağırarak`OnWriteBodyContents` ve arabelleğe `OnWriteStartEnvelope` almadanönce,çağrılarınvarsayılanuygulamasıdır.`OnWriteStartBody` Üstbilgiler yazılmadı.  
  
 Tüm iletinin çeşitli parçalarından oluşturulduğu şekli değiştirmek için yönteminigeçersizkılın.<xref:System.ServiceModel.Channels.Message.OnWriteMessage%2A> Yöntemi, <xref:System.ServiceModel.Channels.Message.WriteMessage%2A> varsayılan<xref:System.ServiceModel.Channels.Message.OnCreateBufferedCopy%2A> uygulamadan ve öğesinden çağrılır. `OnWriteMessage` Geçersiz kılma <xref:System.ServiceModel.Channels.Message.WriteMessage%2A> en iyi yöntem değildir. Uygun `On` yöntemleri geçersiz kılmak daha iyidir ( <xref:System.ServiceModel.Channels.Message.OnWriteStartEnvelope%2A>örneğin <xref:System.ServiceModel.Channels.Message.OnWriteStartHeaders%2A>,, ve <xref:System.ServiceModel.Channels.BodyWriter.OnWriteBodyContents%2A>.  
  
 Hata <xref:System.ServiceModel.Channels.Message.OnBodyToString%2A> ayıklama sırasında ileti gövdesinin nasıl temsil edileceğini geçersiz kılmak için geçersiz kılın. Varsayılan değer, üç nokta ("...") olarak temsil etmektedir. İleti durumu kapalı dışında bir şey olduğunda, bu yöntemin birden çok kez çağrılabilecek olduğunu unutmayın. Bu yöntemin uygulanması asla yalnızca bir kez gerçekleştirilmesi gereken herhangi bir eyleme neden olmamalıdır (yalnızca bir salt iletme akışından okuma gibi).  
  
 SOAP body öğesindeki özniteliklere erişime izin vermek için yönteminigeçersizkılın.<xref:System.ServiceModel.Channels.Message.OnGetBodyAttribute%2A> Bu yöntem herhangi bir sayıda çağrılabilir, ancak `Message` temel tür yalnızca ileti oluşturulduğu durumda olduğunda çağrılabilir. Bir uygulamadaki durumu denetlemek gerekli değildir. Varsayılan uygulama her zaman döndürülür `null`. Bu, gövde öğesinde hiç öznitelik olmadığını gösterir.  
  
 İleti gövdesi artık gerekli olmadığında <xref:System.ServiceModel.Channels.Message.OnClose%2A> nesnenizinözeltemizlikyapmasıgerekiyorsa,geçersizkılabilirsiniz.`Message` Varsayılan uygulama hiçbir şey yapmaz.  
  
 `IsEmpty` Ve`IsFault` özellikleri geçersiz kılınabilir. Varsayılan olarak, her ikisi `false`de döndürülür.
