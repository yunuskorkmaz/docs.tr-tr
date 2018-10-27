---
title: WCF Test İstemcisi (WcfTestClient.exe)
ms.date: 03/30/2017
ms.assetid: d4302855-677f-4640-aa90-c5d785d72fb7
ms.openlocfilehash: 4e3531b91382c4d47aed73198bd8dd954ae4ca1f
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50181598"
---
# <a name="wcf-test-client-wcftestclientexe"></a>WCF Test İstemcisi (WcfTestClient.exe)
Windows Communication Foundation (WCF) Test İstemcisi (WcfTestClient.exe), kullanıcılara test parametreleri giriş, hizmete girdi gönderme olanağı sağlar ve hizmet geri gönderir yanıtı görüntüleyin bir GUI araçtır. Bu test WCF hizmet konağı ile birleştirildiğinde deneyimi sorunsuz bir hizmet sağlar.  
  
 WCF Test İstemcisi (WcfTestClient.exe) genellikle şu konumda bulabilirsiniz: `C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\Common7\IDE` - topluluk "Kurumsal", "Professional" biri olabilir veya Visual Studio'nun hangi düzeyine bağlı olarak "Community" yüklenir.
  
## <a name="scenarios-for-using-test-client"></a>Test İstemcisi'ni kullanmaya yönelik senaryolar  
 Aşağıdaki bölümlerde, WCF Test İstemcisi geliştirme sürecinizi kolaylaştırmak için kullanabileceğiniz en yaygın senaryolar açıklanmaktadır.  
  
### <a name="inside-visual-studio"></a>İç Visual Studio  
  
#### <a name="wcf-service-host-starts-wcf-test-client-with-a-single-service"></a>Tek bir hizmetle WCF hizmet konağı başlatır WCF Test İstemcisi  
 Yeni bir WCF Hizmeti projesi oluşturun ve hata ayıklayıcıyı başlatmak için F5 tuşuna basın, projenizdeki hizmeti barındırmak WCF hizmet konağı başlar. Ardından, WCF Test İstemcisi açar ve hizmet uç noktaları yapılandırma dosyasında tanımlanan bir listesini görüntüler. Test parametreleri ve hizmeti çağırmak ve sürekli olarak test edin ve hizmetinizi doğrulamak için bu işlemi yineleyin.  
  
#### <a name="wcf-service-host-starts-wcf-test-client-with-multiple-services"></a>Birden çok hizmetlerle WCF hizmet konağı başlatır WCF Test İstemcisi  
 WCF Test istemcisi, birden çok hizmeti içeren bir hizmet proje hatalarını ayıklamaya yardımcı olmak için de kullanabilirsiniz. WCF Test İstemcisi açıldığında otomatik olarak projenize hizmetlerin listesi yinelenir ve test etmek için açar.  
  
### <a name="outside-visual-studio"></a>Visual Studio dışında  
 WCF Test İstemcisi (WcfTestClient.exe), Internet üzerindeki bir rastgele hizmeti test etmek için Visual Studio dışında de çağırabilirsiniz. Aracı bulmak için şu konuma gidin:  
  
 `C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\Common7\IDE` (burada topluluk "Kurumsal", "Professional" veya "Community" makinede yüklü Visual Studio düzeyine bağlı olarak olabilir)
  
 Aracı kullanmak için bu konumdan açmak için dosya adına çift tıklayın veya bir komut satırından başlatılamıyor.  
  
 WCF Test istemcisi, komut satırı bağımsız değişkenleri rastgele bir URI'leri sayısını alır.  Bu, test edilebilir hizmetlerinin bir URI'leri ücretlerdir.  
  
 `wcfTestClient.exe URI1 URI2 …`  
  
 WCF Test İstemcisi penceresi açıldıktan sonra tıklayın **dosya**->**Hizmet Ekle**, açmak istediğiniz hizmet uç nokta adresini girin.  
  
## <a name="wcf-test-client-user-interface"></a>WCF Test istemcisi kullanıcı arabirimi  
 WCF Test istemcisi, tek bir hizmeti veya birden çok hizmetlerle kullanabilirsiniz.  
  
### <a name="service-operations"></a>Hizmet işlemleri  
 WCF Test İstemcisi ana pencerenin sol bölmesinde, tüm kullanılabilir hizmetler, ilgili uç noktaları ve işlemleri birlikte listeler.  
  
 Bir işlem çift tıkladığınızda, işlem adı ile yeni bir sekme içinde sağ bölmede içeriği görüntüleyebilirsiniz.  
  
 Sol bölmede, ayrıca istemci yapılandırma dosyalarını listelenir. Herhangi bir öğeyi sağ bölmede yeni bir sekmeli pencerede dosya içeriğini görüntülemek için çift tıklayın.  
  
### <a name="entering-test-parameters"></a>Test parametreleri girme  
 Test parametreleri görüntülemek için bir işlem sağ bölmede açmak için çift tıklayın. Parametreleri olarak gösterilen **biçimlendirilmiş** varsayılan olarak, Görünüm ve parametreler hizmeti test etmek için rastgele değerler girebilirsiniz.  
  
 İletinin XML görüntülemek için tıklayın **XML**. Bunları hizmete göndermek için tıklatın **Invoke**.  
  
 Bir veri kümesi parametresi için tıklatın **...** düğmesinin yanındaki **Düzenle...** DataGrid gösteren yeni bir pencerede düzenlemek için. Fark görünümünü **kopyalama veri kümesi** ve **Yapıştır veri kümesi** düğmeleri. Veri nesnesinin şema ilk düzenleme bilinmiyorsa DataGrid boştur. DataGrid'deki geçerli nesneye bir DataSet nesnesiyle aynı şemaya yapıştırmak zorunda. (Şema yapıştırma işlemi önce başka bir yere kopyalamak gerektiğini unutmayın.) Tıklayarak gelecekte kullanım için bir veri kümesi nesnesi kopyalayabilirsiniz **kopyalama veri kümesi** düğmesi.  
  
 Hizmetin yanıt test parametreleri altında görünür.  
  
> [!NOTE]
>  Beklenen dönüş değeri bir dize ise, bir giriş sağlanmadı tırnak içine değil olsa da sonuç alıntılanmış dize olarak görüntülenir.  
  
 Hizmet sözleşmesini oluşturduğunuzda belirli bir işlem tek yönlü belirttiyseniz, hizmet yanıt görüntülenir. İletinin teslim için sıraya alındı hemen sonra bir iletişim kutusu ileti başarıyla gönderildi bildirmek için açılır.  
  
### <a name="session-support"></a>Oturum desteği  
 **Yeni bir proxy Başlat** hizmet işlemin sekmesindeki onay kutusunu oturum desteği geçiş olanak sağlar. Bu kutuyu, varsayılan olarak işaretli değildir.  
  
 Ne zaman belirli bir işlemi (veya başka bir işlemde aynı hizmet uç noktası) için test parametreleri girin ve tıklayın **Invoke** birden çok kez temizlenmiş onay kutusu ile bir proxy bu işlemleri paylaşın ve hizmet durumu: birden çok işlemde kalıcı.  
  
 Varsa **yeni Proxy'yi başlatın** her biri için yeni bir proxy başlatıldığında, onay kutusunun işaretli **Invoke**önceki oturumu senaryo sona erdi ve hizmet durumu sıfırlanır.  
  
### <a name="editing-client-configuration"></a>Düzenleme istemcisi yapılandırması  
 WCF Test İstemcisi ana pencerenin sol bölmesinde, istemci yapılandırması dosyaları listeler. Herhangi bir öğeyi sağ bölmede dosya içeriğini görüntülemek için çift tıklayın.  
  
#### <a name="edit-with-service-configuration-editor"></a>Hizmet yapılandırma Düzenleyicisi ile düzenleyin  
 Sağ **yapılandırma dosyası** sol bölmesinde seçip bağlam menüsünü **SvcConfigEditor ile Düzenle**. Hizmet yapılandırma Düzenleyicisi ile istemci yapılandırma içeriği başlatılır. Yapılandırmasını düzenleyin ve aracın içinden kaydedin.  
  
 WCF Test istemcisi, hizmet yapılandırma Düzenleyicisi'nde dosyayı kaydettikten sonra dosyanın dışında değiştirildi ve yeniden yüklemek isteyip istemediğinizi soran bir size bildirmek amacıyla kullanıcılara bir uyarı iletisi görüntüler.  
  
 Seçerseniz **Evet**, "Client.dll.config" sekmesindeki yapılandırma içeriği Düzenleyicisi'nde yaptığınız değişiklikleri yansıtır.  
  
 Seçerseniz **Hayır**"Client.dll.config" sekmesindeki yapılandırma içeriği değişmeden kalır ve değiştirilen içerik kaynak dosyayı otomatik olarak kaydedilir.  
  
#### <a name="restore-to-default-configuration"></a>Varsayılan yapılandırmayı geri yükle  
 İstiyorsanız tüm değişiklikleri iptal etmek ve varsayılan istemci yapılandırmasında geri yükleme, sağ **yapılandırma dosyası** sol bölmesinde seçip bağlam menüsünü **varsayılan yapılandırmaya geri**. Varsayılan yapılandırma değeri yüklenir ve içerik "Client.dll.config" sekmesine geri yüklenir.  
  
#### <a name="validate-changes"></a>Değişiklikleri doğrulama  
 WCF Test İstemcisi'nde kaydedilen değişiklikleri yüklenmiş yapılandırma geçerlilik WCF şeması karşı denetlenir. Hata bulunursa, hata ayrıntılarını gösteren bir iletişim kutusu görüntülenir.  
  
 Proxy oluşturma, derleme ikili veya hizmetini çağırmak sırasında (diğer bir deyişle, "Düzenle...", "Geri yükle..." vb.) düzenleme desteği menü öğelerini devre dışı bırakılır. Yükleme için WCF Test istemcisi yapılandırma güncelleştirildiğinde hizmet çağırma de devre dışı bırakılır.  
  
#### <a name="persist-client-configuration"></a>İstemci yapılandırma  
 **Araçları**->**seçenekleri**->**istemci yapılandırması** sekmesini içeren bir **her zaman yeniden yapılandırma, başlatma Hizmetleri** seçeneği, varsayılan olarak etkindir. WCF Test istemcisi hizmet yükleyen her zaman en son hizmet sözleşmesi ve hizmet App.config dosyaları dayalı bir yapılandırma dosyası oluşturur, bu seçenek belirtir.  
  
 İstemci yapılandırması için WCF hizmetinizi düzenlediniz ve her zaman bu güncelleştirilmiş dosya, hizmetinizin işaretini kaldırarak hata ayıklama için kullanmak istediğiniz **yeniden** seçeneği. Hizmet güncelleştirmesi ve WCF Test İstemcisi'ni yeniden bile bunu yaptığınızda, Client.dll.config daha önce bir yeniden oluşturuldu güncelleştirilmiş servisi temel alan bir yerine güncelleştirilmiş bir dosyadır.  
  
 Ancak, yeniden oluşturuldu proxy ile tutarlı hale getirmek için yapılandırma dosyasını düzenlemeniz gerekebilir. Yapılandırma dosyası ve yeniden oluşturuldu proxy nedeniyle güncelleştirilmiş bir hizmet eşleşirse, hizmet çağrıldığında hataları ortaya çıkar.  
  
> [!CAUTION]
>  İstemci yapılandırma dosyası değiştirdiniz ve gelecekte kullanmayı seçerseniz, dosya şu konumda bulabilirsiniz:  
>   
>  \Documents ve ayarları\\[kullanıcı hesabı] \My Documents\Test istemci projeleri.  
>   
>  İstemci yapılandırma dosyasına depolanan tüm güncelleştirilmiş kimlik bilgileri, erişim denetimi listesi (ACL olarak) bu klasörün korunur.  
  
### <a name="adding-removing-and-refreshing-services"></a>Hizmetleri ekleme, kaldırma ve yenileme  
  
#### <a name="add-service"></a>Hizmet Ekle  
 Tıklayın **dosya**->**Hizmet Ekle** WCF Test istemcisi için bir hizmet eklemek için. Ardından, eklenecek URI'sini (uç nokta adresi) hizmet türü için gereklidir. Hizmetin adres bir adresi mex veya WSDL adresi olabilir.  
  
 Son eklenen 10 Hizmetler'in uç noktaların listesini de bulabilirsiniz **on Hizmetler** alt. Bunlardan birini seçerseniz, belirtilen hizmet WCF Test istemcisi için eklenir.  
  
 Ayrıca hizmet ağacının kökü sağ **hizmet Projelerim**seçip **Hizmet Ekle** aynı sonucu elde etmek için.  
  
 Proxy sırasında bir hizmet olarak eklenmesini destekliyordu oluşturma, ikili derleme veya hizmet çağırma menü öğelerini devre dışı bırakıldı. Hizmet çağırma de devre dışı bırakılır.  
  
#### <a name="remove-service"></a>Hizmeti Kaldır  
 Kaldırılacak ve hizmetinin Hizmet kök sağ **hizmeti Kaldır** WCF Test İstemcisi ' bir hizmeti kaldırmak için.  
  
 Proxy sırasında bir hizmeti kaldırma desteği oluşturma, ikili derleme veya hizmet çağırma menü öğelerini devre dışı bırakıldı. Hizmet çağırma de devre dışı bırakılır.  
  
#### <a name="refresh-service"></a>Hizmeti yenileme  
 WCF Test İstemcisi çalıştıran ve bu hizmet için WCF Test İstemcisi uygulama güncel olduğundan emin olmak istediğiniz hizmet için değişiklik yapıldığında, hizmet ve select hizmet kök sağ **hizmeti yenileme**. Yenilendikten sonra hizmet durumunu sıfırlanacağını unutmayın.  
  
 Proxy sırasında hizmet yenileme desteği oluşturma, ikili derleme veya hizmet çağırma menü öğelerini devre dışı bırakıldı. Hizmet çağırma de devre dışı bırakılır.  
  
## <a name="location-of-files-generated-by-the-test-client"></a>Test istemcisi tarafından oluşturulan dosyalarının konumu  
 Varsayılan olarak, WCF Test İstemcisi depoları, istemci kodu ve yapılandırma dosyaları "%appdata%\Local\temp\Test istemci projeleri" klasöründe oluşturulur. Bu klasör, WCF Test İstemcisi çıktıktan sonra silinir. Bir yapılandırma dosyası WCF Test İstemcisi'nde değiştirilip değiştirilmediğini ve **her zaman yeniden yapılandırma, başlatma Hizmetleri** seçeneği devre dışıdır, değiştirilen dosya "Documents\Test istemci Projelerim altındaki"Önbelleğe alınmış yapılandırma"klasörüne kopyalanır "Bir dizin olarak bir eşleme (meta veriler-adresini-için-dosya adı) XML dosyasıyla Documents\Test istemci projeleri.  
  
 WCF Test istemcisi bir komut satırında kullanmak da başlatabilirsiniz `/ProjectPath` oluşturulan dosyalarını depolamak için yeni bir istenen yol belirtmek için geçiş ya da kullanmak `/RestoreProjectPath` varsayılan konuma geri yüklemek için anahtar. Söz dizimi aşağıdaki gibidir:  
  
 `wcfTestClient.exe /ProjectPath [desired location]`  
  
 Bu komutun çalıştırılması WCF Test İstemcisi açılmaz. Klasör konumu değişir. WCF Test istemcisi veya çalışıyor olsun, bu komutu çalıştırabilirsiniz. WCF Test İstemcisi yeniden başlatıldığında yeni konuma uygulanır. Konum bilgileri, kayıt defterindeki ya da "%appdata%\Local\temp\Test istemci projeleri" klasöründe WcfTestClient.exe.option dosyasında kaydedilebilir.  
  
## <a name="features-supported-by-wcf-test-client"></a>WCF Test istemcisi tarafından desteklenen özellikler  
 WCF Test istemcisi tarafından desteklenen özelliklerin bir listesi verilmiştir:  
  
-   Hizmet çağırma: İstek/yanıt ve tek yönlü mesaj.  
  
-   Bağlamaları: Tüm bağlamaları svcutil.exe'yi desteklenir.  
  
-   Oturum denetleme.  
  
-   İleti sözleşmesi.  
  
-   XML serileştirme.  
  
 WCF Test istemcisi tarafından desteklenmeyen özelliklerin bir listesi verilmiştir:  
  
-   Türleri: <xref:System.IO.Stream>, <xref:System.ServiceModel.Channels.Message>, <xref:System.Xml.XmlElement>, <xref:System.Xml.XmlAttribute>, <xref:System.Xml.XmlNode>, türleri uygulayan <xref:System.Xml.Serialization.IXmlSerializable> arabirimi ilgili dahil olmak üzere, <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> özniteliği ve <xref:System.Xml.Linq.XDocument> ve <xref:System.Xml.Linq.XElement> türleri ve ADO.NET <xref:System.Data.DataTable> türü.  
  
-   Çift yönlü sözleşme.  
  
-   İşlem.  
  
-   Güvenlik: [!INCLUDE[infocard](../../../includes/infocard-md.md)] , sertifika ve kullanıcı adı/parola.  
  
-   Bağlamaları: Herhangi bir bağlam bağlamaları ve WebHttpbinding (Json yanıt iletisi desteği), Https bağlamasını WSFederationbinding.  
  
## <a name="closing-wcf-test-client"></a>WCF Test İstemcisi kapatma  
 WCF Test istemcisi aşağıdaki şekilde kapatabilirsiniz:  
  
-   Üzerinde **dosya** menüsünü tıklatın **çıkış**. Alternatif olarak, WCF Test İstemcisi ana penceresinde tıklayın **Kapat**. Hem bu eylemlerden birini de WCF hizmet otomatik konağı kapatın ve WCF Test İstemcisi Visual Studio tarafından başlatıldıysa, Visual Studio hata ayıklama işlemini durdurun.  
  
-   Sağ **WCF hizmet konağı** bildirim alanına ve ardından simge **çıkış.** Bu işlem, WCF hizmeti otomatik konağı ve WCF Test İstemcisi aşağı kapatır ve Visual Studio hata ayıklama işlemi durdurur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF Hizmet Konağı (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)
