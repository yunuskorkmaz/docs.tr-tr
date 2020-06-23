---
title: İleti Sınıfını Kullanma
description: WCF için temel olan Ileti sınıfı hakkında bilgi edinin. Ileti sınıfını doğrudan yalnızca bazı Gelişmiş senaryolarda programla programlama yapmanız gerekir.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d1d62bfb-2aa3-4170-b6f8-c93d3afdbbed
ms.openlocfilehash: f806e257cfd3ccc5118a5783e2eda48eef4ba0bf
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246499"
---
# <a name="using-the-message-class"></a>İleti Sınıfını Kullanma
<xref:System.ServiceModel.Channels.Message>Sınıfı Windows Communication Foundation (WCF) için temel bir sınıftır. İstemciler ve hizmetler arasındaki tüm iletişimler, sonuçta <xref:System.ServiceModel.Channels.Message> gönderilen ve alınan örneklerin sonucu olarak sonuçlanır.  
  
 Genellikle sınıfla doğrudan etkileşim kurmamalıdır <xref:System.ServiceModel.Channels.Message> . Bunun yerine, gelen ve giden iletileri anlatmak için veri sözleşmeleri, ileti sözleşmeleri ve işlem sözleşmeleri gibi WCF hizmet modeli yapıları kullanılır. Ancak, bazı Gelişmiş senaryolarda doğrudan sınıfını kullanarak program programlama yapabilirsiniz <xref:System.ServiceModel.Channels.Message> . Örneğin, sınıfını kullanmak isteyebilirsiniz <xref:System.ServiceModel.Channels.Message> :  
  
- Giden ileti içerikleri oluşturmak için alternatif bir yönteme ihtiyacınız olduğunda (örneğin, diskteki bir dosyadan doğrudan bir ileti oluşturma) .NET Framework nesneleri serileştirmek yerine.  
  
- Gelen ileti içeriklerini (örneğin, Ham XML içeriklerine XSLT dönüştürmesi uygulamak istediğinizde) .NET Framework nesneleri içine çıkarmak yerine farklı bir şekilde kullanmanız gerektiğinde.  
  
- İletileri ileti içeriğinden bağımsız olarak genel bir şekilde (örneğin, yönlendirici oluştururken veya iletme, yük dengeleyici ya da bir yayımlama-abonelik sistemi) kullanmanız gerektiğinde.  
  
 Sınıfını kullanmadan önce <xref:System.ServiceModel.Channels.Message> [veri aktarımı mimarisine genel bakış](data-transfer-architectural-overview.md)' da WCF veri aktarımı mimarisini öğrenin.  
  
 <xref:System.ServiceModel.Channels.Message>, Veriler için genel amaçlı bir kapsayıcıdır, ancak TASARıMı SOAP protokolünde bir iletinin tasarımını yakından izler. SOAP içinde olduğu gibi, bir iletinin hem ileti gövdesi hem de üst bilgileri vardır. İleti gövdesinde gerçek yük verileri bulunur, ancak üstbilgiler adlandırılmış veri kapsayıcıları içerir. Gövde ve üst bilgileri okuma ve yazma kuralları farklıdır; Örneğin, üst bilgilerin her zaman bellekte ara belleğe alınır ve gövde yalnızca bir kez okunabilir ve akış yapılabilir olabilir. Normal olarak, SOAP kullanırken ileti gövdesi SOAP gövdesine eşlenir ve ileti başlıkları SOAP üst bilgilerine eşlenir.  
  
## <a name="using-the-message-class-in-operations"></a>Işlemlerde Ileti sınıfını kullanma  
 <xref:System.ServiceModel.Channels.Message>Sınıfını bir işlemin giriş parametresi, bir işlemin dönüş değeri veya her ikisi de kullanabilirsiniz. <xref:System.ServiceModel.Channels.Message>Bir işlemde herhangi bir yerde kullanılırsa, aşağıdaki kısıtlamalar geçerlidir:  
  
- İşlem herhangi bir `out` veya parametreye sahip olamaz `ref` .  
  
- Birden fazla `input` parametre olamaz. Parametresi varsa, ya Ileti ya da bir ileti sözleşmesi türü olmalıdır.  
  
- Dönüş türü, ya da `void` `Message` bir ileti sözleşmesi türü olmalıdır.  
  
 Aşağıdaki kod örneği geçerli bir işlem sözleşmesi içerir.  
  
 [!code-csharp[C_UsingTheMessageClass#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#1)]
 [!code-vb[C_UsingTheMessageClass#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#1)]  
  
## <a name="creating-basic-messages"></a>Temel Iletileri oluşturma  
 <xref:System.ServiceModel.Channels.Message>Sınıfı, `CreateMessage` temel iletileri oluşturmak için kullanabileceğiniz statik fabrika yöntemleri sağlar.  
  
 Tüm `CreateMessage` Aşırı Yüklemeler, <xref:System.ServiceModel.Channels.MessageVersion> ileti IÇIN kullanılacak soap ve ws-Addressing sürümlerini gösteren türünde bir sürüm parametresi alır. Gelen iletiyle aynı protokol sürümlerini kullanmak istiyorsanız, <xref:System.ServiceModel.OperationContext.IncomingMessageVersion%2A> <xref:System.ServiceModel.OperationContext> özelliğinden elde edilen örnekteki özelliğini kullanabilirsiniz <xref:System.ServiceModel.OperationContext.Current%2A> . Çoğu `CreateMessage` aşırı yüklemenin Ayrıca ileti için kullanılacak soap eylemini gösteren bir dize parametresi vardır. Sürüm, `None` SOAP Zarfı oluşturmayı devre dışı bırakmak için olarak ayarlanabilir; ileti yalnızca gövdeden oluşur.  
  
## <a name="creating-messages-from-objects"></a>Nesnelerden Ileti oluşturma  
 `CreateMessage`Yalnızca bir sürümü alan en temel aşırı yükleme ve bir eylem, boş bir gövdeye sahip bir ileti oluşturur. Başka bir aşırı yükleme ek bir <xref:System.Object> parametre alır; bu, gövdesi verilen nesnenin serileştirilmiş temsili olan bir ileti oluşturur. <xref:System.Runtime.Serialization.DataContractSerializer>Serileştirme için varsayılan ayarlarla kullanın. Farklı bir serileştirici kullanmak istiyorsanız ya da farklı şekilde yapılandırmak istiyorsanız, `DataContractSerializer` `CreateMessage` aynı zamanda bir parametre alan aşırı yüklemeyi kullanın `XmlObjectSerializer` .  
  
 Örneğin, bir iletiye bir nesne döndürmek için aşağıdaki kodu kullanabilirsiniz.  
  
 [!code-csharp[C_UsingTheMessageClass#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#2)]
 [!code-vb[C_UsingTheMessageClass#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#2)]  
  
## <a name="creating-messages-from-xml-readers"></a>XML okuyucularından Ileti oluşturma  
 Bir `CreateMessage` <xref:System.Xml.XmlReader> <xref:System.Xml.XmlDictionaryReader> nesne yerine gövde için bir veya olan aşırı yüklemeler vardır. Bu durumda, iletinin gövdesi, geçirilen XML okuyucusundan okunmadan elde edilen XML 'yi içerir. Örneğin, aşağıdaki kod, gövde içeriği bir XML dosyasından okunan bir ileti döndürür.  
  
 [!code-csharp[C_UsingTheMessageClass#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#3)]
 [!code-vb[C_UsingTheMessageClass#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#3)]  
  
 Buna ek olarak, `CreateMessage` <xref:System.Xml.XmlReader> <xref:System.Xml.XmlDictionaryReader> yalnızca gövde değil, tüm iletiyi temsil eden veya içeren aşırı yüklemeler vardır. Bu aşırı yüklemeler Ayrıca bir tamsayı `maxSizeOfHeaders` parametresi alır. Üst bilgiler, ileti oluşturulduğu anda her zaman bellek olarak arabelleğe alınır ve bu parametre, gerçekleşen arabelleğe alma miktarını sınırlandırır. Bir hizmet reddi saldırısı olasılığını azaltmak için, XML güvenilmeyen bir kaynaktan geliyorsa bu parametrenin güvenli bir değere ayarlanması önemlidir. XML okuyucusunun temsil ettiği iletinin SOAP ve WS-Addressing sürümleri, sürüm parametresi kullanılarak belirtilen sürümlerle eşleşmelidir.  
  
## <a name="creating-messages-with-bodywriter"></a>BodyWriter ile Ileti oluşturma  
 Bir `CreateMessage` aşırı yükleme `BodyWriter` , iletinin gövdesini tanımlayacak bir örnek alır. `BodyWriter`, İleti gövdelerinin nasıl oluşturulduğunu özelleştirmek için türetilebilen soyut bir sınıftır. `BodyWriter`İleti gövdelerini özel bir şekilde anlatmak için kendi türetilmiş sınıfınızı oluşturabilirsiniz. Alan yöntemini geçersiz kılmanız gerekir `BodyWriter.OnWriteBodyContents` <xref:System.Xml.XmlDictionaryWriter> ; Bu yöntem, gövdeyi yazmadan sorumludur.  
  
 Gövde yazıcılarının ara belleğe alınabilir veya ara belleğe alınmamış (akış). Arabelleğe alınmış gövde yazarları içerikleri herhangi bir sayıda yazabilir, ancak akışa alma içerikleri yalnızca bir kez yazılabilir. `IsBuffered`Özelliği, gövde yazıcısının arabelleğe alınıp alınmayacağını gösterir. Bu `BodyWriter` değeri, bir Boolean parametresi alan korumalı oluşturucuyu çağırarak gövde yazıcınız için ayarlayabilirsiniz `isBuffered` . Gövde yazarları, arabelleğe alınmamış bir gövde yazıcısından arabellekli bir gövde yazıcısının oluşturulmasını destekler. `OnCreateBufferedCopy`Bu işlemi özelleştirmek için yöntemini geçersiz kılabilirsiniz. Varsayılan olarak, tarafından döndürülen XML içeren bir bellek içi arabellek `OnWriteBodyContents` kullanılır. `OnCreateBufferedCopy`bir `maxBufferSize` tamsayı parametresi alır; bu yöntemi geçersiz kılarsınız, bu en büyük boyuttan daha büyük arabellekler oluşturmamalıdır.  
  
 `BodyWriter`Sınıfı, `WriteBodyContents` `CreateBufferedCopy` `OnWriteBodyContents` sırasıyla ve yöntemleri etrafında ölçülü sarmalayıcılar olan ve yöntemlerini sağlar `OnCreateBufferedCopy` . Bu yöntemler, arabelleğe alınmamış bir gövde yazıcısında birden çok kez erişilmediğinden emin olmak için durum denetimi gerçekleştirir. Bu yöntemler doğrudan yalnızca öğesine `Message` dayalı özel türetilmiş sınıflar oluşturulurken çağrılır `BodyWriters` .  
  
## <a name="creating-fault-messages"></a>Hata Iletileri oluşturma  
 `CreateMessage`SOAP hata iletileri oluşturmak için belirli aşırı yüklemeleri kullanabilirsiniz. Bunların en temel, <xref:System.ServiceModel.Channels.MessageFault> hatayı açıklayan bir nesne alır. Kolaylık sağlamak için diğer aşırı yüklemeler sunulmaktadır. İlk bu aşırı yükleme bir `FaultCode` ve neden dizesi alır ve `MessageFault` `MessageFault.CreateFault` Bu bilgileri kullanarak bir kullanarak oluşturur. Diğer aşırı yükleme bir ayrıntı nesnesi alır ve ayrıca `CreateFault` hata kodu ve nedeni ile birlikte bir araya geçirir. Örneğin, aşağıdaki işlem bir hata döndürür.  
  
 [!code-csharp[C_UsingTheMessageClass#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#4)]
 [!code-vb[C_UsingTheMessageClass#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#4)]  
  
## <a name="extracting-message-body-data"></a>Ileti gövdesi verileri ayıklanıyor  
 `Message`Sınıfı, gövdeden bilgi ayıklamanın birden çok yolunu destekler. Bunlar aşağıdaki kategorilerde sınıflandırılabilir:  
  
- Tüm ileti gövdesinin bir kez bir XML yazıcı olarak yazılmış şekilde alınması. Bu, *ileti yazma*olarak adlandırılır.  
  
- İleti gövdesi üzerinde bir XML okuyucusu alma. Bu, daha sonra ileti gövdesine gereken şekilde parça erişimini sağlamanıza olanak sağlar. Bu, *ileti okuma*olarak adlandırılır.  
  
- Gövdesi dahil olmak üzere tüm ileti, türün bellek içi arabelleğine kopyalanabilir <xref:System.ServiceModel.Channels.MessageBuffer> . Buna *bir ileti kopyalama*denir.  
  
 `Message`Ne olursa olsun, bir yalnızca bir kez gövdeye erişebilirsiniz. Bir ileti nesnesi `State` , başlangıçta oluşturulması için ayarlanmış olan bir özelliğine sahiptir. Yukarıdaki listede açıklanan üç erişim yöntemi, sırasıyla durum yazılır, okundu ve kopyalanabilir olarak ayarlanır. Ayrıca, `Close` ileti gövdesi içerikleri artık gerekli olmadığında bir yöntem durumu kapalı olarak ayarlayabilir. İleti gövdesine yalnızca oluşturulan durumda erişilebilir ve durum değiştirildikten sonra oluşturulan duruma geri dönmenin bir yolu yoktur.  
  
## <a name="writing-messages"></a>Ileti yazma  
 <xref:System.ServiceModel.Channels.Message.WriteBodyContents%28System.Xml.XmlDictionaryWriter%29>Yöntemi belirli bir örneğin gövde içeriğini `Message` belırlı bir XML yazıcısına yazar. <xref:System.ServiceModel.Channels.Message.WriteBody%2A>Yöntemi, gövde içeriğini uygun sarmalayıcı öğesine (örneğin, <>) içermedikçe aynı şekilde yapar `soap:body` . Son olarak, <xref:System.ServiceModel.Channels.Message.WriteMessage%2A> sarmalama soap Zarfı ve üst bilgileri de dahil olmak üzere tüm iletiyi yazar. SOAP kapalıysa ( <xref:System.ServiceModel.Channels.Message.Version> ise <xref:System.ServiceModel.Channels.MessageVersion.None?displayProperty=nameWithType> ), üç yöntem de aynı şeyi yapar: ileti gövdesi içeriklerini yazar.  
  
 Örneğin, aşağıdaki kod, gelen bir iletinin gövdesini bir dosyaya yazar.  
  
 [!code-csharp[C_UsingTheMessageClass#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#5)]
 [!code-vb[C_UsingTheMessageClass#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#5)]  
  
 İki ek yardımcı yöntem, belirli SOAP başlangıç öğesi etiketlerini yazar. Bu yöntemler ileti gövdesine erişemez ve bu nedenle ileti durumunu değiştirmez. Bu güncelleştirmeler şunlardır:  
  
- <xref:System.ServiceModel.Channels.Message.WriteStartBody%2A>başlangıç gövdesi öğesini (örneğin,) yazar `<soap:Body>` .  
  
- <xref:System.ServiceModel.Channels.Message.WriteStartEnvelope%2A>başlangıç zarfı öğesini (örneğin,) yazar `<soap:Envelope>` .  
  
 Karşılık gelen bitiş öğesi etiketlerini yazmak için `WriteEndElement` ılgılı XML yazıcı üzerinde öğesini çağırın. Bu yöntemler nadiren doğrudan çağırılır.  
  
## <a name="reading-messages"></a>Iletileri okuma  
 Bir ileti gövdesini okumayı sağlamanın birincil yolu, çağrıladır <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> . <xref:System.Xml.XmlDictionaryReader>İleti gövdesini okumak için kullanabileceğiniz bir geri alırsınız. <xref:System.ServiceModel.Channels.Message> <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> Döndürülen XML okuyucusunu kullandığınızda değil, okuma durumuna yapılan geçişlerin çağrılır.  
  
 <xref:System.ServiceModel.Channels.Message.GetBody%2A>Yöntemi, ileti gövdesine türü belirlenmiş bir nesne olarak erişmenizi de sağlar. Dahili olarak, bu yöntem kullanır `GetReaderAtBodyContents` ve ayrıca ileti durumunu <xref:System.ServiceModel.Channels.MessageState.Read> duruma geçirir (bkz <xref:System.ServiceModel.Channels.Message.State%2A> . özelliği).  
  
 Özelliğini denetlemek iyi <xref:System.ServiceModel.Channels.Message.IsEmpty%2A> bir uygulamadır, bu durumda ileti gövdesi boştur ve <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> bir oluşturur <xref:System.InvalidOperationException> . Ayrıca, alınan bir iletidir (örneğin, yanıt), <xref:System.ServiceModel.Channels.Message.IsFault%2A> iletinin bir hata içerip içermediğini belirten denetlemek de isteyebilirsiniz.  
  
 ' Nin en temel aşırı yüklemesi, <xref:System.ServiceModel.Channels.Message.GetBody%2A> <xref:System.Runtime.Serialization.DataContractSerializer> varsayılan ayarlarla yapılandırılmış ve <xref:System.Runtime.Serialization.DataContractSerializer.MaxItemsInObjectGraph%2A> kotasının devre dışı bırakıldığı bir tür örneğine (genel parametresiyle belirtilir) ileti gövdesini serileştirir. Farklı bir serileştirme altyapısı kullanmak veya `DataContractSerializer` varsayılan olmayan bir şekilde yapılandırmak istiyorsanız, <xref:System.ServiceModel.Channels.Message.GetBody%2A> alan aşırı yüklemeyi kullanın <xref:System.Runtime.Serialization.XmlObjectSerializer> .  
  
 Örneğin, aşağıdaki kod serileştirilmiş bir nesne içeren bir ileti gövdesinden verileri ayıklar `Person` ve kişinin adını yazdırır.  
  
 [!code-csharp[C_UsingTheMessageClass#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#6)]
 [!code-vb[C_UsingTheMessageClass#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#6)]  
  
## <a name="copying-a-message-into-a-buffer"></a>Bir Iletiyi arabelleğe kopyalama  
 Bazen ileti gövdesine birden çok kez erişmek gerekir, örneğin, aynı iletiyi Yayımcı-abone sisteminin bir parçası olarak birden fazla hedefe iletmek için. Bu durumda, bellekteki tüm iletiyi (gövde dahil) arabelleğe almak gereklidir. Bunu çağırarak yapabilirsiniz <xref:System.ServiceModel.Channels.Message.CreateBufferedCopy%28System.Int32%29> . Bu yöntem, en büyük arabellek boyutunu temsil eden bir tamsayı parametresi alır ve bu boyuttan daha büyük olmayan bir arabellek oluşturur. İleti güvenilmeyen bir kaynaktan geliyorsa bunu güvenli bir değere ayarlamanız önemlidir.  
  
 Arabellek bir örnek olarak döndürülür <xref:System.ServiceModel.Channels.MessageBuffer> . Arabellekteki verilere çeşitli yollarla erişebilirsiniz. Birincil yol, <xref:System.ServiceModel.Channels.Message.CreateMessage%2A> arabellekteki örnekleri oluşturmak için çağrıladır `Message` .  
  
 Arabellekteki verilere erişmenin başka bir yolu, <xref:System.Xml.XPath.IXPathNavigable> <xref:System.ServiceModel.Channels.MessageBuffer> sınıfın temel alınan XML 'e doğrudan erişmek için uyguladığı arabirimi uygulamaktır. Bazı <xref:System.ServiceModel.Channels.MessageBuffer.CreateNavigator%2A> aşırı yüklemeler <xref:System.Xml.XPath> , bir düğüm kotasıyla korunan ve zıyaret edilecek XML düğümlerinin sayısını sınırlayan gezintiler oluşturmanızı sağlar. Bu, uzun işlem süresine göre hizmet reddi saldırılarını önlemeye yardımcı olur. Bu teklif varsayılan olarak devre dışıdır. Bazı `CreateNavigator` aşırı yüklemeler <xref:System.Xml.XmlSpace> , varsayılan değer olarak, sabit LISTESINI kullanarak XML 'de ne kadar boşluk işleneceğini belirtmenizi sağlar `XmlSpace.None` .  
  
 İleti arabelleğinin içeriğine erişmenin son bir yolu, kullanarak içeriğini bir akışa yazmaktır <xref:System.ServiceModel.Channels.Message.WriteMessage%2A> .  
  
 Aşağıdaki örnek, ile çalışma sürecini gösterir `MessageBuffer` : gelen bir ileti birden çok alıcıya iletilir ve sonra bir dosyaya kaydedilir. Arabelleğe alma olmadan bu mümkün değildir, çünkü ileti gövdesine yalnızca bir kez erişilebilir.  
  
 [!code-csharp[C_UsingTheMessageClass#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#7)]
 [!code-vb[C_UsingTheMessageClass#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#7)]  
  
 `MessageBuffer`Sınıfı, başka üyelere dikkat edin. Bu <xref:System.ServiceModel.Channels.MessageBuffer.Close%2A> Yöntem, arabellek içerikleri artık gerekli olmadığında kaynakları serbest bırakmak için çağrılabilir. <xref:System.ServiceModel.Channels.MessageBuffer.BufferSize%2A>Özelliği, ayrılan arabelleğin boyutunu döndürür. <xref:System.ServiceModel.Channels.MessageBuffer.MessageContentType%2A>Özelliği ILETININ MIME içerik türünü döndürür.  
  
## <a name="accessing-the-message-body-for-debugging"></a>Hata ayıklama için Ileti gövdesine erişme  
 Hata ayıklama amacıyla, <xref:System.ServiceModel.Channels.Message.ToString%2A> bir dize olarak iletinin gösterimini almak için yöntemini çağırabilirsiniz. Bu gösterim genellikle, metin kodlayıcıyla kodlanmışsa, XML 'in insanlar okunabilirlik için daha iyi biçimlendirildiğinden emin olmak dışında, bir iletinin bir ileti ile kodlanması ile aynı şekilde ele alınmasıdır. Bunun tek istisnası ileti gövdesidir. Gövde yalnızca bir kez okunabilir ve `ToString` ileti durumunu değiştirmez. Bu nedenle, `ToString` Yöntem gövdeye erişebilmeyebilir ve bir yer tutucuyu (örneğin, "...") kullanabilir. ya da üç nokta) ileti gövdesi yerine. Bu nedenle, `ToString` iletilerin gövde içeriği önemliyse iletileri günlüğe kaydetmek için kullanmayın.  
  
## <a name="accessing-other-message-parts"></a>Diğer Ileti bölümlerine erişme  
 Gövde içerikleri dışındaki iletiyle ilgili bilgilere erişmek için çeşitli özellikler sağlanır. Ancak, ileti kapatıldıktan sonra bunlar çağrılamaz:  
  
- <xref:System.ServiceModel.Channels.Message.Headers%2A>Özelliği ileti üstbilgilerini temsil eder. Bu konunun ilerleyen kısımlarında yer alan "üstbilgileriyle çalışma" bölümüne bakın.  
  
- <xref:System.ServiceModel.Channels.Message.Properties%2A>Özelliği, ileti gönderildiğinde genellikle yayınlanmayan iletiye eklenen adlandırılmış veri parçaları olan ileti özelliklerini temsil eder. Bu konunun ilerleyen kısımlarında yer alan "özelliklerle çalışma" bölümüne bakın.  
  
- <xref:System.ServiceModel.Channels.Message.Version%2A>Özelliği, iletiyle ILIŞKILI SOAP ve ws-Addressing sürümünü, ya da `None` SOAP devre dışı olduğunu gösterir.  
  
- <xref:System.ServiceModel.Channels.Message.IsFault%2A>Özelliği, `true` ILETI bir SOAP hata iletisi ise döndürür.  
  
- <xref:System.ServiceModel.Channels.Message.IsEmpty%2A>Özelliği, `true` ileti boşsa döndürür.  
  
 <xref:System.ServiceModel.Channels.Message.GetBodyAttribute%28System.String%2CSystem.String%29> `<soap:Body>` Belirli bir ad ve ad alanı tarafından tanımlanan gövde sarmalayıcı öğesi (örneğin,) üzerinde belirli bir özniteliğe erişmek için yöntemini kullanabilirsiniz. Böyle bir öznitelik bulunamazsa, `null` döndürülür. Bu yöntem yalnızca `Message` oluşturma durumunda olduğunda çağrılabilir (ileti gövdesine henüz erişilmemişse).  
  
## <a name="working-with-headers"></a>Üstbilgileriyle çalışma  
 `Message`, *Üst bilgiler*olarak adlandırılan herhangi BIR sayıda adlandırılmış XML parçacığı içerebilir. Her parça normalde bir SOAP üstbilgisiyle eşlenir. Üst bilgilere, `Headers` türünün özelliği aracılığıyla erişilir <xref:System.ServiceModel.Channels.MessageHeaders> . <xref:System.ServiceModel.Channels.MessageHeaders>bir <xref:System.ServiceModel.Channels.MessageHeaderInfo> nesne koleksiyonudur ve tek bir üst bilgiye kendi <xref:System.Collections.IEnumerable> arabiriminden ya da onun Dizin Oluşturucusu aracılığıyla erişilebilir. Örneğin, aşağıdaki kod, içindeki tüm üstbilgilerin adlarını listeler `Message` .  
  
 [!code-csharp[C_UsingTheMessageClass#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#8)]
 [!code-vb[C_UsingTheMessageClass#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#8)]  
  
#### <a name="adding-removing-finding-headers"></a>Üst bilgileri ekleme, kaldırma, bulma  
 Yöntemini kullanarak tüm mevcut üstbilgilerin sonuna yeni bir üst bilgi ekleyebilirsiniz <xref:System.ServiceModel.Channels.MessageHeaders.Add%2A> . <xref:System.ServiceModel.Channels.MessageHeaders.Insert%2A>Belirli bir dizine üst bilgi eklemek için yöntemini kullanabilirsiniz. Eklenen öğe için mevcut üstbilgiler kaydırılacağı. Üst bilgiler, dizinlerine göre sıralanır ve kullanılabilir ilk dizin 0 ' dır. <xref:System.ServiceModel.Channels.MessageHeaders.CopyHeadersFrom%2A>Farklı bir veya örneğinden üst bilgi eklemek için çeşitli yöntem yüklerini kullanabilirsiniz `Message` `MessageHeaders` . Bazı aşırı yüklemeler tek bir üst bilgiyi kopyalar, diğerleri ise tümünü kopyalar. <xref:System.ServiceModel.Channels.MessageHeaders.Clear%2A>Yöntemi tüm üst bilgileri kaldırır. <xref:System.ServiceModel.Channels.MessageHeaders.RemoveAt%2A>Yöntemi belirli bir dizindeki bir üst bilgiyi kaldırır (sonrasında tüm üst bilgileri kaydırma). <xref:System.ServiceModel.Channels.MessageHeaders.RemoveAll%2A>Yöntemi, belirli bir ad ve ad alanı ile tüm üstbilgileri kaldırır.  
  
 Yöntemini kullanarak belirli bir üst bilgiyi alın <xref:System.ServiceModel.Channels.MessageHeaders.FindHeader%2A> . Bu yöntem, bulunacak üstbilginin adını ve ad alanını alır ve dizinini döndürür. Üst bilgi birden çok kez oluşursa, bir özel durum oluşturulur. Üst bilgi bulunamazsa,-1 döndürür.  
  
 SOAP üstbilgi modelinde, üst bilgilerin `Actor` amaçlanan alıcıyı belirten bir değeri olabilir. En temel `FindHeader` aşırı yükleme yalnızca iletinin son alıcısı için tasarlanan üstbilgileri arar. Ancak, başka bir aşırı yükleme, aramaya hangi `Actor` değerlerin ekleneceğini belirtmenize olanak sağlar. Daha fazla bilgi için bkz. SOAP belirtimi.  
  
 Bir <xref:System.ServiceModel.Channels.MessageHeaders.CopyTo%28System.ServiceModel.Channels.MessageHeaderInfo%5B%5D%2CSystem.Int32%29> koleksiyondaki üst bilgileri bir nesne dizisine kopyalamak için bir yöntem sağlanır <xref:System.ServiceModel.Channels.MessageHeaders> <xref:System.ServiceModel.Channels.MessageHeaderInfo> .  
  
 Bir başlıktaki XML verilerine erişmek için, <xref:System.ServiceModel.Channels.MessageHeaders.GetReaderAtHeader%2A> belirli bir üst bilgi dizini için BIR XML okuyucusu çağırabilir ve döndürebilirsiniz. Üst bilgi içeriğini bir nesne veya diğer aşırı yüklerden birini kullanarak seri durumdan çıkarmak istiyorsanız <xref:System.ServiceModel.Channels.MessageHeaders.GetHeader%60%601%28System.Int32%29> . En temel aşırı yüklemeler varsayılan şekilde yapılandırılmış kullanılarak üst bilgilerin serisini kaldıramıyor <xref:System.Runtime.Serialization.DataContractSerializer> . Farklı bir serileştirici veya farklı bir yapılandırması kullanmak istiyorsanız `DataContractSerializer` , bir kullanan aşırı yüklemelerin birini kullanın `XmlObjectSerializer` . Ayrıca üst bilgi adını, ad alanını ve isteğe bağlı olarak bir dizin yerine bir değer listesini alan aşırı yüklemeler de vardır `Actor` ; Bu bir `FindHeader` ve birleşimidir `GetHeader` .  
  
## <a name="working-with-properties"></a>Özelliklerle çalışma  
 Bir `Message` örnek rastgele türlerde adlandırılmış nesneleri rastgele bir dizi içerebilir. Bu koleksiyona, `Properties` türünün özelliği aracılığıyla erişilir `MessageProperties` . Koleksiyon <xref:System.Collections.Generic.IDictionary%602> arabirimini uygular ve öğesinden öğesine eşleme görevi görür <xref:System.String> <xref:System.Object> . Normalde, özellik değerleri doğrudan iletinin herhangi bir bölümüne doğrudan eşlenmiyor, ancak WCF kanal yığınındaki veya hizmet çerçevesindeki çeşitli kanallara çeşitli ileti işleme ipuçları sağlar <xref:System.ServiceModel.Channels.MessageHeaders.CopyTo%28System.ServiceModel.Channels.MessageHeaderInfo%5B%5D%2CSystem.Int32%29> . Bir örnek için bkz. [veri aktarımı mimari genel bakış](data-transfer-architectural-overview.md).  
  
## <a name="inheriting-from-the-message-class"></a>Ileti sınıfından devralma  
 Kullanılarak oluşturulan yerleşik ileti türleri `CreateMessage` gereksinimlerinizi karşılamıyorsa, sınıfından türetilen bir sınıf oluşturun `Message` .  
  
### <a name="defining-the-message-body-contents"></a>Ileti gövdesi Içeriğini tanımlama  
 İleti gövdesinde verilere erişmek için üç birincil teknik mevcuttur: bir arabelleğe yazma, okuma ve bu verileri kopyalama. Bu işlemler, sonunda, <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%2A> ve ' <xref:System.ServiceModel.Channels.Message.OnGetReaderAtBodyContents%2A> <xref:System.ServiceModel.Channels.Message.OnCreateBufferedCopy%2A> ın türetilmiş sınıfınıza sırasıyla,, ve yöntemlerinin çağrılmakta olduğunu sonuç olarak sonuçlanır `Message` . Temel `Message` sınıf, her örnek için yalnızca bir tane Bu yöntemden bir kez çağrıldığına `Message` ve bir kereden fazla çağrılmadığından emin olur. Temel sınıf Ayrıca yöntemlerin kapalı bir ileti üzerinde çağrılmamasını sağlar. Uygulamanızda ileti durumunun izlenmesi gerekmez.  
  
 <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%2A>soyut bir yöntemdir ve uygulanması gerekir. İletinizin gövde içeriğini tanımlamanın en temel yolu bu yöntemi kullanarak yazmalıdır. Örneğin, aşağıdaki ileti 1 ile 20 arasında 100.000 rastgele sayı içerir.  
  
 [!code-csharp[C_UsingTheMessageClass#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#9)]
 [!code-vb[C_UsingTheMessageClass#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#9)]  
  
 <xref:System.ServiceModel.Channels.Message.OnGetReaderAtBodyContents>Ve <xref:System.ServiceModel.Channels.Message.OnCreateBufferedCopy%2A> yöntemlerinin çoğu durumda çalışan varsayılan uygulamaları vardır. Varsayılan uygulamalar çağrı <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%2A> yapın, sonuçları arabelleğe alarak elde edilen arabellekten çalışır. Ancak, bazı durumlarda bu yeterli olmayabilir. Yukarıdaki örnekte, iletiyi okumak 100.000 XML öğelerinin arabelleğe alındığı, bu da istenmeyebilir. <xref:System.ServiceModel.Channels.Message.OnGetReaderAtBodyContents>Rastgele sayılar sunan özel bir türetilmiş sınıf döndürmek için geçersiz kılmak isteyebilirsiniz <xref:System.Xml.XmlDictionaryReader> . Ardından, <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%2A> <xref:System.ServiceModel.Channels.Message.OnGetReaderAtBodyContents> Aşağıdaki örnekte gösterildiği gibi, yöntemin döndürdüğü okuyucuyu kullanmak için geçersiz kılabilirsiniz.  
  
 [!code-csharp[C_UsingTheMessageClass#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#10)]
 [!code-vb[C_UsingTheMessageClass#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#10)]  
  
 Benzer şekilde, `OnCreateBufferedCopy` kendi türetilmiş sınıfınızı döndürmek için geçersiz kılmak isteyebilirsiniz `MessageBuffer` .  
  
 İleti gövdesi içerikleri sağlamaya ek olarak, iletiniz türetilmiş sınıfınız,, ve özelliklerini de geçersiz kılmalıdır `Version` `Headers` `Properties` .  
  
 İletinin bir kopyasını oluşturursanız, kopyanın başlangıçtaki ileti üstbilgilerini kullandığını unutmayın.  
  
### <a name="other-members-that-can-be-overridden"></a>Geçersiz kılınabilen diğer Üyeler  
 <xref:System.ServiceModel.Channels.Message.OnWriteStartEnvelope%2A> <xref:System.ServiceModel.Channels.Message.OnWriteStartHeaders%2A> <xref:System.ServiceModel.Channels.Message.OnWriteStartBody%2A> SOAP Zarfı, SOAP üstbilgileri ve SOAP gövdesi öğe başlangıç etiketlerinin nasıl yazıldığını belirtmek için, ve yöntemlerini geçersiz kılabilirsiniz. Bunlar normalde, ve ' a karşılık gelir `<soap:Envelope>` `<soap:Header>` `<soap:Body>` . Bu yöntemler normalde, özelliği döndürürse bir şeyi yazmamalıdır <xref:System.ServiceModel.Channels.Message.Version> <xref:System.ServiceModel.Channels.MessageVersion.None> .  
  
> [!NOTE]
> `OnGetReaderAtBodyContents`Çağrıları `OnWriteStartEnvelope` `OnWriteStartBody` çağırarak ve arabelleğe almadan önce, çağrıların varsayılan uygulamasıdır `OnWriteBodyContents` . Üstbilgiler yazılmadı.  
  
 <xref:System.ServiceModel.Channels.Message.OnWriteMessage%2A>Tüm iletinin çeşitli parçalarından oluşturulduğu şekli değiştirmek için yöntemini geçersiz kılın. `OnWriteMessage`Yöntemi, <xref:System.ServiceModel.Channels.Message.WriteMessage%2A> varsayılan uygulamadan ve öğesinden çağrılır <xref:System.ServiceModel.Channels.Message.OnCreateBufferedCopy%2A> . Geçersiz kılma <xref:System.ServiceModel.Channels.Message.WriteMessage%2A> en iyi yöntem değildir. Uygun yöntemleri geçersiz kılmak daha iyidir `On` (örneğin,, <xref:System.ServiceModel.Channels.Message.OnWriteStartEnvelope%2A> <xref:System.ServiceModel.Channels.Message.OnWriteStartHeaders%2A> ve <xref:System.ServiceModel.Channels.BodyWriter.OnWriteBodyContents%2A> .  
  
 <xref:System.ServiceModel.Channels.Message.OnBodyToString%2A>Hata ayıklama sırasında ileti gövdesinin nasıl temsil edileceğini geçersiz kılmak için geçersiz kılın. Varsayılan değer, üç nokta ("...") olarak temsil etmektedir. İleti durumu kapalı dışında bir şey olduğunda, bu yöntemin birden çok kez çağrılabilecek olduğunu unutmayın. Bu yöntemin uygulanması asla yalnızca bir kez gerçekleştirilmesi gereken herhangi bir eyleme neden olmamalıdır (yalnızca bir salt iletme akışından okuma gibi).  
  
 <xref:System.ServiceModel.Channels.Message.OnGetBodyAttribute%2A>SOAP body öğesindeki özniteliklere erişime izin vermek için yöntemini geçersiz kılın. Bu yöntem herhangi bir sayıda çağrılabilir, ancak `Message` temel tür yalnızca Ileti oluşturulduğu durumda olduğunda çağrılabilir. Bir uygulamadaki durumu denetlemek gerekli değildir. Varsayılan uygulama her zaman döndürülür `null` . Bu, gövde öğesinde hiç öznitelik olmadığını gösterir.  
  
 `Message`İleti gövdesi artık gerekli olmadığında nesnenizin özel temizlik yapması gerekiyorsa, geçersiz kılabilirsiniz <xref:System.ServiceModel.Channels.Message.OnClose%2A> . Varsayılan uygulama hiçbir şey yapmaz.  
  
 `IsEmpty`Ve `IsFault` özellikleri geçersiz kılınabilir. Varsayılan olarak, her ikisi de döndürülür `false` .
