---
title: WCF Test İstemcisi (WcfTestClient.exe)
ms.date: 03/30/2017
ms.assetid: d4302855-677f-4640-aa90-c5d785d72fb7
ms.openlocfilehash: 78be40268b46c4c85ee034db67d67ee0fbf2158f
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33809751"
---
# <a name="wcf-test-client-wcftestclientexe"></a>WCF Test İstemcisi (WcfTestClient.exe)
Windows Communication Foundation (WCF) Test İstemcisi (WcfTestClient.exe), kullanıcılara giriş test parametreleri, bu hizmete giriş gönderme olanağı sağlar ve hizmet geri gönderdiği yanıt görüntülemek bir GUI aracıdır. WCF hizmet ana bilgisayarı ile birleştirildiğinde deneyimi sınama sorunsuz bir hizmet sağlar.  
  
 WCF Test İstemcisi (WcfTestClient.exe) genellikle şu konumda bulabilirsiniz: C:\Program Files (x86) \Microsoft Visual Studio\2017\Community\Common7\IDE - topluluk biri olabilir "Kuruluş", "Profesyonel" veya "üzerinde bağlı olarak topluluk" Visual Studio düzeyini yüklenir.
  
## <a name="scenarios-for-using-test-client"></a>Test İstemcisi kullanma senaryoları  
 Aşağıdaki bölümlerde, WCF Test İstemcisi geliştirme sürecini kolaylaştırmak için kullanabileceğiniz en yaygın senaryolar açıklanmaktadır.  
  
### <a name="inside-visual-studio"></a>İç Visual Studio  
  
#### <a name="wcf-service-host-starts-wcf-test-client-with-a-single-service"></a>WCF hizmet ana bilgisayarı başlatır WCF Test istemcisi tek bir hizmetle  
 Yeni bir WCF Hizmeti projesi oluşturun ve hata ayıklayıcısı başlatmak için F5 tuşuna basarak sonra hizmet projenizdeki barındırmak WCF hizmet konağı başlar. Ardından, WCF Test İstemcisi açar ve yapılandırma dosyasında tanımlanmış hizmet uç noktaları listesini görüntüler. Parametreleri test ve hizmetini çağırmak ve sürekli test ve hizmetinizi doğrulamak için bu işlemi yineleyin.  
  
#### <a name="wcf-service-host-starts-wcf-test-client-with-multiple-services"></a>WCF hizmet ana bilgisayarı başlatır WCF Test İstemcisi birden çok hizmetleriyle  
 WCF Test istemcisi, birden çok hizmet içeren bir hizmet projenin hata ayıklamasını yardımcı olmak için de kullanabilirsiniz. WCF Test İstemcisi açıldığında, otomatik olarak projenizdeki Hizmetleri listesini tarar ve test etmek için açar.  
  
### <a name="outside-visual-studio"></a>Dış Visual Studio  
 WCF Test İstemcisi (WcfTestClient.exe), Internet üzerindeki rasgele bir hizmet test etmek için Visual Studio dışında de çalıştırabilirsiniz. Aracı bulmak için aşağıdaki konuma gidin:  
  
 C:\Program Files\Microsoft Visual Studio 9.0\Common7\IDE\  
  
 Aracı kullanmak için bu konumdan açmak için dosya adına çift tıklayın veya bir komut satırından başlatın.  
  
 WCF Test İstemcisi URI'ler rastgele sayıda komut satırı bağımsız değişkenleri olarak alır.  Test edilebilir Hizmetleri URI'ler bunlar.  
  
 `wcfTestClient.exe URI1 URI2 …`  
  
 WCF Test İstemcisi penceresi açıldıktan sonra tıklatın **dosya**->**Hizmet Ekle**, açmak istediğiniz hizmet uç noktası adresi girin.  
  
## <a name="wcf-test-client-user-interface"></a>WCF Test istemcisi kullanıcı arabirimi  
 WCF Test istemcisi tek bir hizmeti veya birden çok hizmet ile kullanabilirsiniz.  
  
### <a name="service-operations"></a>Hizmet işlemleri  
 WCF Test İstemcisi ana penceresinin sol bölmesinde kullanılabilen tüm hizmetler, kendi ilgili uç noktaları ve işlemleri ile birlikte listeler.  
  
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
 WCF Test İstemcisi ana penceresinin sol bölmesinde istemci yapılandırma dosyaları listelenmektedir. Sağ bölmede dosyasının içeriğini görüntülemek için öğeleri çift tıklayın.  
  
#### <a name="edit-with-service-configuration-editor"></a>Hizmet yapılandırma Düzenleyicisi ile düzenleyin  
 Sağ **yapılandırma dosyası** sol bölmesinde seçip bağlam menüsünü **SvcConfigEditor ile düzenleme**. Hizmet yapılandırma Düzenleyicisi ile istemci yapılandırma içeriği başlatılır. Yapılandırmasını düzenleyin ve aracın içinden kaydedin.  
  
 WCF Test İstemcisi hizmeti yapılandırma Düzenleyicisi'nde dosya kaydedildikten sonra dosyanın dışında değiştirilmiş ve yeniden isteyip istemediğinizi soran hakkında bilgilendirmek için bir uyarı iletisi görüntüler.  
  
 Seçerseniz **Evet**, "Client.dll.config" sekmesinde yapılandırma içeriği Düzenleyicisi'nde yaptığınız değişiklikleri yansıtır.  
  
 Seçerseniz **Hayır**, "Client.dll.config" sekmesinde yapılandırma içerik değişmeden kalır ve değiştirilen içerik otomatik olarak kaynak dosyasına kaydedilir.  
  
#### <a name="restore-to-default-configuration"></a>Varsayılan yapılandırmayı geri yükleme  
 İstiyorsanız, tüm değişiklikleri iptal etmek ve varsayılan istemci yapılandırmasında geri yüklemek için sağ **yapılandırma dosyası** sol bölmesinde seçip bağlam menüsünü **geri yüklemek için varsayılan yapılandırma**. Varsayılan yapılandırma değeri yüklenir ve "Client.dll.config" sekmesini içeriğinde geri yüklenir.  
  
#### <a name="validate-changes"></a>Değişiklikleri doğrulama  
 WCF Test İstemcisi değişiklikleri kaydedildi yüklenmiş yapılandırma WCF şemayla geçerliliğini denetlenir. Hata bulunursa hata ayrıntılarını görüntülemek için bir iletişim kutusu görüntülenir.  
  
 Proxy oluşturması, ikili derleme veya hizmet çağırma sırasında (diğer bir deyişle, "Düzenle...", "Geri..." vb.) düzenleme desteği menü öğelerini devre dışı. Yükleme için WCF Test istemcisi yapılandırma güncelleştirildiği hizmet başlatma de devre dışı bırakılır.  
  
#### <a name="persist-client-configuration"></a>İstemci yapılandırması Sürdür  
 **Araçları**->**seçenekleri**->**istemci yapılandırması** sekmesini içeren bir **her zaman yeniden yapılandırma, başlatma Hizmetleri** seçeneği varsayılan olarak etkindir. Bu seçenek, bir hizmet WCF Test İstemcisi yükleyen her zaman, bu en son hizmet sözleşmesini ve hizmet App.config dosyaları dayalı bir yapılandırma dosyası oluşturur belirtir.  
  
 İstemci yapılandırması WCF hizmetiniz için düzenlediniz ve her zaman bu güncelleştirilmiş dosya kutusunun işaretini kaldırın, hizmette hata ayıklamak için kullanmak istediğiniz **yeniden** seçeneği. Güncelleştirme hizmeti ve WCF Test istemcisi, yeniden bile bunu yaparak, Client.dll.config daha önce yeniden biri güncelleştirilmiş hizmetini temel alan yerine güncelleştirilmiş bir dosyadır.  
  
 Ancak, yeniden proxy ile tutarlı hale getirmek için yapılandırma dosyasını düzenlemenize gerekebilir. Yapılandırma dosyası ve yeniden proxy nedeniyle güncelleştirilmiş bir hizmet eşleşirse, hizmet çağrıldığında hatalar ortaya çıkar.  
  
> [!CAUTION]
>  İstemci yapılandırma dosyası değiştirdiniz ve gelecekte yeniden kullanmayı seçerseniz, dosyası şu konumda bulabilirsiniz:  
>   
>  \Documents and Settings\\[kullanıcı hesabı] \My Documents\Test istemci projeleri.  
>   
>  İstemci yapılandırma dosyasına depolanmış güncelleştirilmiş kimlik bilgileri, erişim denetim listesi (ACL tarafından), bu klasörün korunur.  
  
### <a name="adding-removing-and-refreshing-services"></a>Ekleme, kaldırma ve Hizmetleri yenileme  
  
#### <a name="add-service"></a>Hizmet Ekle  
 Tıklatın **dosya**->**Hizmet Ekle** WCF Test istemcisi için bir hizmet eklemek için. Eklenecek URI'sini (uç nokta adresi) hizmet türü için gereklidir. Hizmetin adresi mex adresi veya WSDL adresi olabilir.  
  
 10 son eklenen hizmetlerin uç noktalarını listesini bulabileceğiniz **son Hizmetleri** alt. Bunlardan birini seçerseniz, belirtilen hizmet WCF Test İstemcisi eklenir.  
  
 Ayrıca hizmet ağacının kökü sağ **My hizmeti projeleri**seçip **Hizmet Ekle** aynı sonucu elde etmek için.  
  
 Proxy sırasında bir hizmeti ekleme desteği oluşturma, ikili derleme ya da hizmet başlatma menü öğelerini devre dışı bırakılır. Hizmet başlatma de devre dışı bırakılır.  
  
#### <a name="remove-service"></a>Hizmeti Kaldır  
 Hizmet kök hizmetinin kaldırılması ve seçmek için sağ **hizmeti Kaldır** WCF Test istemciden bir hizmeti kaldırmak için.  
  
 Proxy sırasında bir hizmeti kaldırma desteği oluşturma, ikili derleme ya da hizmet başlatma menü öğelerini devre dışı bırakılır. Hizmet başlatma de devre dışı bırakılır.  
  
#### <a name="refresh-service"></a>Hizmet Yenile  
 Bir değişiklik hizmete WCF Test İstemcisi çalıştığından ve hizmetin WCF Test İstemcisi uygulaması güncel olduğundan emin olmak istediğiniz sırada yapılırsa, hizmet kök hizmeti ve seçin sağ **yenileme Hizmet**. Yenilendikten sonra hizmet durumu sıfırlanır unutmayın.  
  
 Proxy sırasında bir hizmeti yenilemeyi destekleyen oluşturma, ikili derleme ya da hizmet başlatma menü öğelerini devre dışı bırakılır. Hizmet başlatma de devre dışı bırakılır.  
  
## <a name="location-of-files-generated-by-the-test-client"></a>Test istemcisi tarafından üretilen dosyalarının konumu  
 Varsayılan olarak, WCF Test İstemcisi depoları istemci kodu ve yapılandırma dosyaları "%appdata%\Local\temp\Test istemci projeleri" klasöründe oluşturulur. Bu klasör, WCF Test İstemcisi çıktıktan sonra silinir. Bir yapılandırma dosyası WCF Test İstemcisi değiştirilip değiştirilmediğini ve **her zaman yeniden yapılandırma, başlatma Hizmetleri** seçeneği devre dışıdır, değiştirilen dosya "My Documents\Test istemci projeleri altındaki"Önbelleğe alınmış yapılandırma"klasörüne kopyalanır Bir eşleme (meta verileri-adres-için-dosya adı) XML dosyası olarak bir dizin ile Documents\Test istemci projeleri".  
  
 WCF Test istemcisi komut satırında, kullanım başlatabilirsiniz `/ProjectPath` oluşturulan dosyaları depolamak için yeni bir istenen yolunu belirtmek için geçiş ya da kullanmak `/RestoreProjectPath` varsayılan konuma geri yüklemek için anahtar. Söz dizimi aşağıdaki gibidir:  
  
 `wcfTestClient.exe /ProjectPath [desired location]`  
  
 Bu komutu çalıştırmak, WCF Test İstemcisi açılmaz. Yalnızca klasör konumu değiştirilir. WCF Test istemcisi veya çalışıp çalışmadığını bu komutu çalıştırabilirsiniz. WCF Test İstemcisi yeniden başlatıldığında yeni konumu uygulanır. Konum bilgileri, kayıt defterindeki ya da "%appdata%\Local\temp\Test istemci projeleri" klasöründe WcfTestClient.exe.option dosyasında kaydedilebilir.  
  
## <a name="features-supported-by-wcf-test-client"></a>WCF Test istemcisi tarafından desteklenen özellikler  
 WCF Test istemcisi tarafından desteklenen özelliklerin bir listesi verilmiştir:  
  
-   Hizmet başlatma: İstek/yanıt ve tek yönlü ileti.  
  
-   Bağlamaları: Tüm bağlamaları Svcutil.exe tarafından desteklenir.  
  
-   Oturum denetleme.  
  
-   İleti sözleşmesi.  
  
-   XML serileştirme.  
  
 WCF Test istemcisi tarafından desteklenmeyen özelliklerin bir listesi verilmiştir:  
  
-   Türleri: <xref:System.IO.Stream>, <xref:System.ServiceModel.Channels.Message>, <xref:System.Xml.XmlElement>, <xref:System.Xml.XmlAttribute>, <xref:System.Xml.XmlNode>, türleri uygulayan <xref:System.Xml.Serialization.IXmlSerializable> arabirimi ilgili dahil olmak üzere, <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> özniteliği ve <xref:System.Xml.Linq.XDocument> ve <xref:System.Xml.Linq.XElement> türleri ve ADO.NET <xref:System.Data.DataTable> türü.  
  
-   Çift yönlü sözleşme.  
  
-   İşlem.  
  
-   Güvenlik: [!INCLUDE[infocard](../../../includes/infocard-md.md)] , sertifika ve kullanıcı adı/parola.  
  
-   Bağlamaları: WSFederationbinding, herhangi bir bağlam bağlamalar ve Https bağlaması, WebHttpbinding (Json yanıt iletisi desteği).  
  
## <a name="closing-wcf-test-client"></a>WCF Test İstemcisi kapatma  
 WCF Test istemcisi aşağıdaki yollarla kapatabilirsiniz:  
  
-   Üzerinde **dosya** menüsünde tıklatın **çıkış**. Alternatif olarak, WCF Test İstemcisi ana penceresinde **Kapat**. Hem bu eylem ayrıca WCF hizmeti otomatik konak kapatın ve WCF Test İstemcisi Visual Studio tarafından başlatılan, Visual Studio hata ayıklama işlemini durdurun.  
  
-   Sağ **WCF hizmet konağı** bildirim alanına ve ardından simge **çıkış.** Bu WCF hizmeti otomatik ana bilgisayarı ve WCF Test İstemcisi aşağı kapatır ve Visual Studio hata ayıklama işlemi durdurur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF Hizmet Konağı (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)
