---
title: "WCF Test İstemcisi (WcfTestClient.exe)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d4302855-677f-4640-aa90-c5d785d72fb7
caps.latest.revision: "45"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 28098a4e598d1c3bede3b05e3afe1001c3944d42
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="wcf-test-client-wcftestclientexe"></a>WCF Test İstemcisi (WcfTestClient.exe)
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)]Test İstemcisi (WcfTestClient.exe), kullanıcılara giriş test parametreleri, bu hizmete giriş gönderme olanağı sağlar ve hizmet geri gönderdiği yanıt görüntülemek bir GUI aracıdır. İle birleştirildiğinde deneyimi sınama sorunsuz bir hizmet sunar [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmet ana bilgisayarı.  
  
 Bulabileceğiniz [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Test İstemcisi (WcfTestClient.exe) aşağıdaki konumda: C:\Program Files\Microsoft Visual Studio 9.0\Common7\IDE\  
  
## <a name="scenarios-for-using-test-client"></a>Test İstemcisi kullanma senaryoları  
 Aşağıdaki bölümlerde içinde kullanabileceğiniz en yaygın senaryolar açıklanmaktadır [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] geliştirme sürecini kolaylaştırmak için Test istemcisi.  
  
### <a name="inside-visual-studio"></a>İç Visual Studio  
  
#### <a name="wcf-service-host-starts-wcf-test-client-with-a-single-service"></a>WCF hizmet ana bilgisayarı başlatır WCF Test istemcisi tek bir hizmetle  
 Yeni bir oluşturduktan sonra [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmet projesi ve hata ayıklayıcı başlatmak için F5 tuşuna basarak [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] projenizdeki hizmet ana bilgisayar için hizmet ana bilgisayarı başlar. Ardından, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Test İstemcisi açar ve yapılandırma dosyasında tanımlanmış hizmet uç noktaları listesini görüntüler. Parametreleri test ve hizmetini çağırmak ve sürekli test ve hizmetinizi doğrulamak için bu işlemi yineleyin.  
  
#### <a name="wcf-service-host-starts-wcf-test-client-with-multiple-services"></a>WCF hizmet ana bilgisayarı başlatır WCF Test İstemcisi birden çok hizmetleriyle  
 Aynı zamanda [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] birden fazla hizmet içeren bir hizmet projenin hata ayıklamasını yardımcı olmak için Test istemcisi. Zaman [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Test İstemcisi açıldığında, otomatik olarak projenizdeki Hizmetleri listesini tarar ve test etmek için açar.  
  
### <a name="outside-visual-studio"></a>Dış Visual Studio  
 Ayrıca çağırabileceği [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Test İstemcisi (WcfTestClient.exe) Internet rasgele bir hizmette test etmek için Visual Studio dışında. Aracı bulmak için aşağıdaki konuma gidin:  
  
 C:\Program Files\Microsoft Visual Studio 9.0\Common7\IDE\  
  
 Aracı kullanmak için bu konumdan açmak için dosya adına çift tıklayın veya bir komut satırından başlatın.  
  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]Test İstemcisi rasgele bir URI sayısı komut satırı bağımsız değişkenleri olarak alır.  Test edilebilir Hizmetleri URI'ler bunlar.  
  
 `wcfTestClient.exe URI1 URI2 …`  
  
 Sonra [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Test İstemcisi penceresi açıldığında, tıklatın **dosya**->**Hizmet Ekle**, açmak istediğiniz hizmet uç noktası adresi girin.  
  
## <a name="wcf-test-client-user-interface"></a>WCF Test istemcisi kullanıcı arabirimi  
 Kullanabileceğiniz [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Test istemcisi tek bir hizmet veya birden çok hizmet.  
  
### <a name="service-operations"></a>Hizmet işlemleri  
 Sol bölmesinde [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Test İstemcisi ana penceresi tüm kullanılabilir hizmetler, kendi ilgili uç noktaları ve işlemleri ile birlikte listeler.  
  
 Bir işlem çift tıkladığınızda, işlem adı ile yeni bir sekme içinde sağ bölmede içeriği görüntüleyebilirsiniz.  
  
 Sol bölmede, ayrıca istemci yapılandırma dosyaları listelenmektedir. Sağ bölmede yeni sekmeli pencerede dosyanın içeriğini görüntülemek için öğeleri çift tıklayın.  
  
### <a name="entering-test-parameters"></a>Test parametreleri girme  
 Test parametreleri görüntülemek için bir işlem sağ bölmede açmak için çift tıklayın. İçinde parametreleri gösterdi **biçimlendirilmiş** varsayılan olarak, Görünüm ve hizmeti sınamak parametreler için rastgele değerler girebilirsiniz.  
  
 İleti XML görüntülemek için **XML**. Hizmete göndermek için tıklatın **Invoke**.  
  
 Bir veri kümesi parametresi için tıklatın **...** düğmesine **Düzenle...** DataGrid gösteren yeni bir pencerede düzenlemek için. Görünümünü fark **Copy DataSet** ve **Yapıştır DataSet** düğmeler. Veri kümesi nesnesi şeması ilk düzenleme bilinmiyorsa DataGrid boştur. DataGrid geçerli nesne bir veri kümesi nesnesi aynı şema yapıştırmak zorunda. (Şema yapıştırma işlemi önce başka bir yere kopyalayın gerektiğini unutmayın.) Tıklayarak gelecekte kullanım için bir veri kümesi nesnesi kopyalayabilirsiniz **Copy DataSet** düğmesi.  
  
 Hizmetin yanıt test parametreleri altında görüntülenir.  
  
> [!NOTE]
>  Beklenen dönüş değeri bir dize ise, sağlanan girdi tırnak içine değildi olsa bile sonucu tırnak içine alınmış bir dize olarak görüntülenir.  
  
 Hizmet sözleşmesini oluşturduğunuzda belirli bir işlem tek yönlü belirttiyseniz, hizmet yanıt görüntülenir. İleti teslim için sıraya hemen bir iletişim kutusu iletisi başarıyla gönderildi bildirmek için açılır.  
  
### <a name="session-support"></a>Oturum desteği  
 **Yeni bir proxy Başlat** hizmet işlemin sekmesindeki onay kutusunu oturum desteğini geçiş olanak sağlar. Bu kutu varsayılan olarak işaretli değildir.  
  
 Ne zaman belirli bir işlemi (veya başka bir işlemde aynı hizmet uç noktası) için test parametreleri girin ve tıklayın **Invoke** birden çok kez onay kutusunu ile bu işlemlerin bir proxy paylaşma ve hizmet durumu: birden çok işlemler arasındaki kalıcı.  
  
 Varsa **yeni bir proxy Başlat** onay kutusu seçiliyse, yeni bir proxy her başlatıldığında **Invoke**önceki oturum senaryo sona erdi ve hizmet durumunu sıfırlayın.  
  
### <a name="editing-client-configuration"></a>İstemci yapılandırması düzenleme  
 Sol bölmesinde [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Test İstemcisi ana penceresi istemcisi yapılandırma dosyalarını listeler. Sağ bölmede dosyasının içeriğini görüntülemek için öğeleri çift tıklayın.  
  
#### <a name="edit-with-service-configuration-editor"></a>Hizmet yapılandırma Düzenleyicisi ile düzenleyin  
 Sağ **yapılandırma dosyası** sol bölmesinde seçip bağlam menüsünü **SvcConfigEditor ile düzenleme**. Hizmet yapılandırma Düzenleyicisi ile istemci yapılandırma içeriği başlatılır. Yapılandırmasını düzenleyin ve aracın içinden kaydedin.  
  
 Hizmet yapılandırma Düzenleyicisi'nde, dosyayı kaydettikten sonra [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Test İstemcisi dosyayı dışında değiştirilmiş ve yeniden isteyip istemediğinizi soran bildirmek için bir uyarı iletisi görüntüler.  
  
 Seçerseniz **Evet**, "Client.dll.config" sekmesinde yapılandırma içeriği Düzenleyicisi'nde yaptığınız değişiklikleri yansıtır.  
  
 Seçerseniz **Hayır**, "Client.dll.config" sekmesinde yapılandırma içerik değişmeden kalır ve değiştirilen içerik otomatik olarak kaynak dosyasına kaydedilir.  
  
#### <a name="restore-to-default-configuration"></a>Varsayılan yapılandırmayı geri yükleme  
 İstiyorsanız, tüm değişiklikleri iptal etmek ve varsayılan istemci yapılandırmasında geri yüklemek için sağ **yapılandırma dosyası** sol bölmesinde seçip bağlam menüsünü **geri yüklemek için varsayılan yapılandırma**. Varsayılan yapılandırma değeri yüklenir ve "Client.dll.config" sekmesini içeriğinde geri yüklenir.  
  
#### <a name="validate-changes"></a>Değişiklikleri doğrulama  
 Ne zaman kaydedilen değişiklikleri yüklenir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Test istemcisi yapılandırma geçerlilik karşı denetlenir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] şema. Hata bulunursa hata ayrıntılarını görüntülemek için bir iletişim kutusu görüntülenir.  
  
 Proxy oluşturması, ikili derleme veya hizmet çağırma sırasında (diğer bir deyişle, "Düzenle...", "Geri..." vb.) düzenleme desteği menü öğelerini devre dışı. Hizmet başlatma de devre dışı yükleme için yapılandırma güncelleştirildiği [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Test istemcisi.  
  
#### <a name="persist-client-configuration"></a>İstemci yapılandırması Sürdür  
 **Araçları**->**seçenekleri**->**istemci yapılandırması** sekmesini içeren bir **her zaman yeniden yapılandırma, başlatma Hizmetleri** seçeneği varsayılan olarak etkindir. Bu seçenek her zaman belirtir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Test istemcisi hizmet yükler, en son hizmet sözleşmesini ve hizmet App.config dosyaları dayalı bir yapılandırma dosyası yeniden oluşturur.  
  
 İstemci yapılandırması düzenlediyseniz, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmeti ve her zaman hizmetinizi hata ayıklamak için bu güncelleştirilmiş dosya kullanmak istiyorsanız, işaretini **yeniden** seçeneği. Yaparak bu nedenle, hatta zaman hizmeti güncelleştirin ve yeniden [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Test İstemcisi Client.dll.config dosyasıdır güncelleştirilmiş size daha önce yeniden güncelleştirilmiş hizmette alan yerine bir.  
  
 Ancak, yeniden proxy ile tutarlı hale getirmek için yapılandırma dosyasını düzenlemenize gerekebilir. Yapılandırma dosyası ve yeniden proxy nedeniyle güncelleştirilmiş bir hizmet eşleşirse, hizmet çağrıldığında hatalar ortaya çıkar.  
  
> [!CAUTION]
>  İstemci yapılandırma dosyası değiştirdiniz ve gelecekte yeniden kullanmayı seçerseniz, dosyası şu konumda bulabilirsiniz:  
>   
>  \Documents and Settings\\[kullanıcı hesabı] \My Documents\Test istemci projeleri.  
>   
>  İstemci yapılandırma dosyasına depolanmış güncelleştirilmiş kimlik bilgileri, erişim denetim listesi (ACL tarafından), bu klasörün korunur.  
  
### <a name="adding-removing-and-refreshing-services"></a>Ekleme, kaldırma ve Hizmetleri yenileme  
  
#### <a name="add-service"></a>Hizmet Ekle  
 Tıklatın **dosya**->**Hizmet Ekle** bir hizmet eklemek için [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Test istemcisi. Eklenecek URI'sini (uç nokta adresi) hizmet türü için gereklidir. Hizmetin adresi mex adresi veya WSDL adresi olabilir.  
  
 10 son eklenen hizmetlerin uç noktalarını listesini bulabileceğiniz **son Hizmetleri** alt. Bunlardan birini seçerseniz, belirtilen hizmet eklenen [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Test istemcisi.  
  
 Ayrıca hizmet ağacının kökü sağ **My hizmeti projeleri**seçip **Hizmet Ekle** aynı sonucu elde etmek için.  
  
 Proxy sırasında bir hizmeti ekleme desteği oluşturma, ikili derleme ya da hizmet başlatma menü öğelerini devre dışı bırakılır. Hizmet başlatma de devre dışı bırakılır.  
  
#### <a name="remove-service"></a>Hizmeti Kaldır  
 Hizmet kök hizmetinin kaldırılması ve seçmek için sağ **hizmeti Kaldır** bir hizmetten kaldırmak için [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Test istemcisi.  
  
 Proxy sırasında bir hizmeti kaldırma desteği oluşturma, ikili derleme ya da hizmet başlatma menü öğelerini devre dışı bırakılır. Hizmet başlatma de devre dışı bırakılır.  
  
#### <a name="refresh-service"></a>Hizmet Yenile  
 Hizmet bir değişiklik yaptıysanız [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Test İstemcisi çalıştığından ve emin olmak istediğiniz [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] bu hizmet için Test İstemcisi uygulaması güncel olup, hizmetin hizmet kök sağ tıklayın ve seçin **Yenile Hizmet**. Yenilendikten sonra hizmet durumu sıfırlanır unutmayın.  
  
 Proxy sırasında bir hizmeti yenilemeyi destekleyen oluşturma, ikili derleme ya da hizmet başlatma menü öğelerini devre dışı bırakılır. Hizmet başlatma de devre dışı bırakılır.  
  
## <a name="location-of-files-generated-by-the-test-client"></a>Test istemcisi tarafından üretilen dosyalarının konumu  
 Varsayılan olarak, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Test İstemcisi depoları istemci kodu ve yapılandırma dosyaları "%appdata%\Local\temp\Test istemci projeleri" klasöründe oluşturulur. Bu klasör sonra silinir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Test İstemcisi çıkar. Bir yapılandırma dosyası içinde değiştirilirse [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Test istemcisi ve **her zaman yeniden yapılandırma, başlatma Hizmetleri** seçeneği devre dışıdır, değiştirilen dosya "My Documents\Test altındaki"Önbelleğe alınmış yapılandırma"klasörüne kopyalanır İstemci projeleri Documents\Test istemci projelerle"bir eşleme (meta verileri-adres-için-dosya adı) XML dosyası olarak bir dizin.  
  
 De başlatabilirsiniz [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] bir komut satırı Test istemcisinde `/ProjectPath` oluşturulan dosyaları depolamak için yeni bir istediğiniz yolu belirtin veya geçiş yapın, kullanın `/RestoreProjectPath` varsayılan konuma geri yüklemek için anahtar. Söz dizimi aşağıdaki gibidir:  
  
 `wcfTestClient.exe /ProjectPath [desired location]`  
  
 Bu komut açık değil çalışan [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Test istemcisi. Yalnızca klasör konumu değiştirilir. Bu komutu çalıştırmak isteyip [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] veya Test İstemcisi çalıştıran. Yeni konumu uygulandığı zaman [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Test İstemcisi yeniden başlatılır. Konum bilgileri, kayıt defterindeki ya da "%appdata%\Local\temp\Test istemci projeleri" klasöründe WcfTestClient.exe.option dosyasında kaydedilebilir.  
  
## <a name="features-supported-by-wcf-test-client"></a>WCF Test istemcisi tarafından desteklenen özellikler  
 Tarafından desteklenen özelliklerin bir listesi aşağıda verilmiştir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Test İstemcisi:  
  
-   Hizmet başlatma: İstek/yanıt ve tek yönlü ileti.  
  
-   Bağlamaları: Tüm bağlamaları Svcutil.exe tarafından desteklenir.  
  
-   Oturum denetleme.  
  
-   İleti sözleşmesi.  
  
-   XML serileştirme.  
  
 Tarafından desteklenmeyen özelliklerin bir listesi aşağıda verilmiştir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Test İstemcisi:  
  
-   Türleri: <xref:System.IO.Stream>, <xref:System.ServiceModel.Channels.Message>, <xref:System.Xml.XmlElement>, <xref:System.Xml.XmlAttribute>, <xref:System.Xml.XmlNode>, türleri uygulayan <xref:System.Xml.Serialization.IXmlSerializable> arabirimi ilgili dahil olmak üzere, <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> özniteliği ve <xref:System.Xml.Linq.XDocument> ve <xref:System.Xml.Linq.XElement> türleri ve ADO.NET <xref:System.Data.DataTable> türü.  
  
-   Çift yönlü sözleşme.  
  
-   İşlem.  
  
-   Güvenlik: [!INCLUDE[infocard](../../../includes/infocard-md.md)] , sertifika ve kullanıcı adı/parola.  
  
-   Bağlamaları: WSFederationbinding, herhangi bir bağlam bağlamalar ve Https bağlaması, WebHttpbinding (Json yanıt iletisi desteği).  
  
## <a name="closing-wcf-test-client"></a>WCF Test İstemcisi kapatma  
 Kapatabilirsiniz [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aşağıdaki yollarla Test İstemcisi:  
  
-   Üzerinde **dosya** menüsünde tıklatın **çıkış**. Alternatif olarak, içinde [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Test İstemcisi ana penceresinde, tıklatın **Kapat**. Bu eylemlerden her ikisi de kapatma [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmeti otomatik ana bilgisayarı ve durdurma [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] işlemi, hata ayıklama [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Test istemcisi tarafından başlatılmış [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].  
  
-   Sağ **WCF hizmet konağı** bildirim alanına ve ardından simge **çıkış.** Bu hem kapatır [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmeti otomatik ana bilgisayarı ve [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Test istemcisi ve durduğunda [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] işlem hata ayıklama.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF Hizmet Konağı (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)
