---
title: WCF Test İstemcisi (WcfTestClient.exe)
ms.date: 03/30/2017
ms.assetid: d4302855-677f-4640-aa90-c5d785d72fb7
ms.openlocfilehash: 56074bf051478e9da1bc11479284883f7321bd63
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916794"
---
# <a name="wcf-test-client-wcftestclientexe"></a>WCF Test İstemcisi (WcfTestClient.exe)
Windows Communication Foundation (WCF) test Istemcisi (WcfTestClient. exe), kullanıcıların test parametreleri girmesini, bu girişi hizmete göndermesini ve hizmetin geri gönderdiği yanıtı görüntülemesini sağlayan bir GUI aracıdır. WCF hizmet ana bilgisayarı ile birleştirildiğinde sorunsuz bir hizmet testi deneyimi sağlar.  
  
 Genellikle WCF test istemcisini (WcfTestClient. exe) şu konumda bulabilirsiniz: `C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\Common7\IDE` -topluluk, hangi Visual Studio düzeyine bağlı olarak "Kurumsal", "profesyonel" veya "topluluk" olabilir.
  
## <a name="scenarios-for-using-test-client"></a>Test Istemcisi kullanma senaryoları  
 Aşağıdaki bölümlerde, geliştirme işleminizi kolaylaştırmak için WCF test Istemcisini kullanabileceğiniz en yaygın senaryolar ele alınmaktadır.  
  
### <a name="inside-visual-studio"></a>Visual Studio 'Nun içinde  
  
#### <a name="wcf-service-host-starts-wcf-test-client-with-a-single-service"></a>WCF hizmet ana bilgisayarı, WCF test Istemcisini tek bir hizmetle başlatır  
 Yeni bir WCF hizmeti projesi oluşturduktan ve hata ayıklayıcıyı başlatmak için F5 'e bastıktan sonra, WCF hizmeti ana bilgisayarı, hizmeti projenizde barındırmaya başlar. Ardından, WCF test Istemcisi açılır ve yapılandırma dosyasında tanımlanan hizmet uç noktalarının listesini görüntüler. Parametreleri test edebilir ve hizmeti çağırabilir ve hizmetinizi sürekli olarak test etmek ve doğrulamak için bu işlemi yineleyebilirsiniz.  
  
#### <a name="wcf-service-host-starts-wcf-test-client-with-multiple-services"></a>WCF hizmet ana bilgisayarı, WCF test Istemcisini birden çok hizmetle başlatır  
 Ayrıca, birden çok hizmet içeren bir hizmet projesinde hata ayıklamanıza yardımcı olması için WCF test Istemcisi de kullanabilirsiniz. WCF test Istemcisi açıldığında, projenizdeki hizmetlerin listesini otomatik olarak yineler ve test için açar.  
  
### <a name="outside-visual-studio"></a>Visual Studio 'Nun dışında  
 Ayrıca, Internet 'te rastgele bir hizmeti test etmek için Visual Studio dışında WCF test Istemcisini (WcfTestClient. exe) çağırabilirsiniz. Aracı bulmak için şu konuma gidin:  
  
 `C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\Common7\IDE`(Bu, topluluk "Kurumsal", "profesyonel" veya "topluluk" olabilir ve makinede hangi Visual Studio düzeyinin yüklü olduğuna bağlı olarak)
  
 Aracı kullanmak için dosya adına çift tıklayarak bu konumdan açın veya bir komut satırından başlatın.  
  
 WCF test Istemcisi, komut satırı bağımsız değişkenleri olarak rastgele sayıda URI alır.  Bunlar, test edilecek hizmetlerin URI 'Lerdir.  
  
 `wcfTestClient.exe URI1 URI2 …`  
  
 WCF Test istemcisi penceresi açıldıktan sonra **Dosya**->**Ekle hizmeti**' ne tıklayın ve açmak istediğiniz hizmetin uç nokta adresini girin.  
  
## <a name="wcf-test-client-user-interface"></a>WCF test Istemcisi Kullanıcı arabirimi  
 WCF test Istemcisini, tek bir hizmet veya birden çok hizmet ile kullanabilirsiniz.  
  
### <a name="service-operations"></a>Hizmet İşlemleri  
 WCF test Istemcisi ana penceresinin sol bölmesi, tüm kullanılabilir hizmetleri, ilgili uç noktaları ve işlemleriyle birlikte listeler.  
  
 Bir işleme çift tıkladığınızda, içeriğini sağ bölmedeki işlemin adına sahip yeni bir sekme içinde görüntüleyebilirsiniz.  
  
 Sol bölmede istemci yapılandırma dosyaları da listelenir. Sağ bölmedeki yeni bir sekmeli pencerede dosyanın içeriğini göstermek için öğelerin herhangi birine çift tıklayın.  
  
### <a name="entering-test-parameters"></a>Test parametreleri giriliyor  
 Test parametrelerini görüntülemek için, sağ bölmede açmak üzere bir işleme çift tıklayın. Parametreler varsayılan olarak **biçimlendirilen** görünümde gösterilir ve hizmeti test etmek için parametreler için rastgele değerler girebilirsiniz.  
  
 İletinin XML 'sini görüntülemek için **XML**' ye tıklayın. Onları hizmete göndermek için **çağır**' a tıklayın.  
  
 Bir veri kümesi parametresi için **.** . düğme, Düzenle ' nin yanında **...** DataGrid ' i gösteren yeni bir pencerede düzenlemek için. **Veri kümesini Kopyala** ve **veri kümesini Yapıştır** düğmelerinin görünümüne dikkat edin. DataSet nesnesinin şeması ilk düzenleme sonrasında bilinmiyorsa, DataGrid boştur. DataGrid içindeki geçerli nesneye aynı şemaya sahip bir veri kümesi nesnesi yapıştırmanız gerekir. (Yapıştırma işleminden önce şemayı başka bir yerde kopyalamanız gerektiğini unutmayın.) Ayrıca, **veri kümesini Kopyala** düğmesine tıklayarak gelecekteki kullanımlar Için bir veri kümesi nesnesi kopyalayabilirsiniz.  
  
 Hizmetin yanıtı test parametrelerinin altında görünür.  
  
> [!NOTE]
> Beklenen dönüş değeri bir dize ise, girilen giriş tırnak içine alınmadığı halde, sonuç tırnak içine alınmış bir dize olarak görüntülenecektir.  
  
 Hizmet için sözleşmeyi oluştururken belirli bir işlemi tek yönlü olarak belirttiyseniz, hizmet yanıtı gösterilmez. İleti teslim için sıraya alındığı anda iletinin başarıyla gönderildiğini bildirmek için bir iletişim kutusu açılır.  
  
### <a name="session-support"></a>Oturum desteği  
 Bir hizmet işleminin sekmesindeki **Yeni bir ara sunucu Başlat** onay kutusu, oturum desteğini yapmanızı sağlar. Bu kutu varsayılan olarak temizlenir.  
  
 Belirli bir işlem (veya aynı hizmet uç noktasındaki başka bir işlem) için test parametreleri girdiğinizde ve onay kutusuyla birden çok kez **çağır** ' a tıkladığınızda, bu işlemler bir ara sunucu paylaşır ve hizmet durumu birden çok kez kalıcıdır operasyonları.  
  
 **Yeni bir ara sunucu Başlat** onay kutusu işaretliyse, her **Invoke**için yeni bir ara sunucu başlatılır, önceki oturum senaryosu sonlandırılır ve hizmet durumu sıfırlanır.  
  
### <a name="editing-client-configuration"></a>Istemci yapılandırması düzenleniyor  
 WCF test Istemcisi ana penceresinin sol bölmesi istemci yapılandırma dosyalarını listeler. Sağ bölmedeki dosyanın içeriğini göstermek için öğelerin herhangi birine çift tıklayın.  
  
#### <a name="edit-with-service-configuration-editor"></a>Hizmet yapılandırma Düzenleyicisi ile Düzenle  
 Sol bölmedeki **yapılandırma dosyası** ' na sağ tıklayın ve **SvcConfigEditor ile Düzenle**bağlam menüsünü seçin. Hizmet yapılandırma Düzenleyicisi, istemci yapılandırma içeriğiyle başlatılır. Yapılandırmayı düzenleyebilir ve araç içine kaydedebilirsiniz.  
  
 Dosyayı hizmet yapılandırma düzenleyicisine kaydettikten sonra, WCF test Istemcisi, dosyanın dışında değiştirildiğini bildiren bir uyarı iletisi görüntüler ve yeniden yüklemek isteyip istemediğinizi sorar.  
  
 **Evet**' i seçerseniz, "Client. dll. config" sekmesindeki yapılandırma içeriği düzenleyicide yaptığınız değişiklikleri yansıtır.  
  
 **Hayır**' ı seçerseniz, "Client. dll. config" sekmesindeki yapılandırma içeriği değişmeden kalır ve değiştirilen içerik otomatik olarak kaynak dosyasına kaydedilir.  
  
#### <a name="restore-to-default-configuration"></a>Varsayılan yapılandırmaya geri yükle  
 Tüm değişiklikleri iptal etmek ve varsayılan istemci yapılandırmasına geri yüklemek istiyorsanız sol bölmedeki **yapılandırma dosyası** ' na sağ tıklayın ve bağlam menüsünü **varsayılan yapılandırmaya geri yükle**' yi seçin. Varsayılan yapılandırma değeri yüklendi ve "Client. dll. config" sekmesindeki İçerik geri yüklendi.  
  
#### <a name="validate-changes"></a>Değişiklikleri doğrula  
 Kaydedilen değişiklikler WCF test Istemcisine yüklenirken, yapılandırma, WCF şemasına karşı geçerliliğini denetledi. Hatalar bulunursa, hata ayrıntılarını göstermek için bir iletişim kutusu görüntülenir.  
  
 Ara sunucu oluşturma, ikili derleme veya hizmet çağırma sırasında, düzenlemeyi destekleyen menü öğeleri (yani, "Düzenle...", "restore...", vb.) devre dışı bırakılır. Güncelleştirilmiş yapılandırma WCF test Istemcisine yüklenirken de hizmet çağrısı devre dışı bırakılır.  
  
#### <a name="persist-client-configuration"></a>Istemci yapılandırmasını kalıcı yap  
 **Araçlar**->**Seçenekler** **istemci yapılandırması** sekmesi, varsayılan olarak etkinleştirilen **Hizmetler seçeneği başlatılırken her zaman yeniden oluştur yapılandırmasını** içerir.-> Bu seçenek, WCF test Istemcisi 'nin bir hizmeti yükleyeceği her seferinde, en son hizmet sözleşmesi ve Service App. config dosyalarına göre bir yapılandırma dosyasını yeniden oluşturur.  
  
 WCF hizmetiniz için istemci yapılandırmasını düzenlediyseniz ve hizmetinize hata ayıklamak için her zaman bu güncelleştirilmiş dosyayı kullanmak istiyorsanız, yeniden **Oluştur** seçeneğinin işaretini kaldırabilirsiniz. Bunu yaparak, hizmeti güncelleştirdiğinizde ve WCF test Istemcisini yeniden açtığınızda bile, güncelleştirilmiş hizmete bağlı olarak bir yeniden üretilme yerine, Client. dll. config dosyası önceden güncelleştirmiş olursunuz.  
  
 Ancak, yeniden üretilen ara sunucu ile tutarlı olması için yapılandırma dosyasını düzenlemeniz gerekebilir. Güncelleştirilmiş bir hizmet nedeniyle yeniden üretilen proxy ve yapılandırma dosyası uyuşiyorsa, hizmet çağrıldığında hatalar oluşur.  
  
> [!CAUTION]
>  İstemci yapılandırma dosyasını değiştirdiyseniz ve gelecekte yeniden kullanmayı seçerseniz, dosyayı aşağıdaki konumda bulabilirsiniz:  
>   
>  \Documents and Settings\\[Kullanıcı hesabı] \Belgelerim\test istemci projeleri.  
>   
>  İstemci yapılandırma dosyasına depolanan güncelleştirilmiş kimlik bilgileri, bu klasörün Access Control listesi (ACL) tarafından korunur.  
  
### <a name="adding-removing-and-refreshing-services"></a>Hizmetleri ekleme, kaldırma ve yenileme  
  
#### <a name="add-service"></a>Hizmet Ekle  
 WCF test istemcisine bir hizmet eklemek için **Dosya**->**ekleme hizmeti** ' ne tıklayın. Daha sonra eklenecek hizmetin URI 'sini (uç nokta adresi) yazmanız gerekir. Hizmetin adresi bir MEX adresi veya WSDL adresi olabilir.  
  
 **Son hizmetler** alt menüsünde son eklenen 10 hizmet uç noktalarının listesini de bulabilirsiniz. Bunlardan birini seçerseniz, belirtilen hizmet WCF test Istemcisine eklenir.  
  
 Ayrıca, hizmet ağacı **sitem projelerimin**köküne sağ tıklayıp **Hizmet Ekle** ' yi seçerek aynı sonucu elde edebilirsiniz.  
  
 Ara sunucu oluşturma, ikili derleme veya hizmet çağrısı sırasında, hizmet eklemeyi destekleyen menü öğeleri devre dışı bırakılır. Hizmet çağrısı da devre dışı bırakılır.  
  
#### <a name="remove-service"></a>Hizmeti Kaldır  
 Kaldırılacak hizmetin hizmet köküne sağ tıklayın ve WCF test Istemcisinden bir hizmeti kaldırmak için **hizmeti Kaldır** ' ı seçin.  
  
 Ara sunucu oluşturma, ikili derleme veya hizmet çağrısı sırasında, bir hizmeti kaldırmayı destekleyen menü öğeleri devre dışı bırakılır. Hizmet çağrısı da devre dışı bırakılır.  
  
#### <a name="refresh-service"></a>Hizmeti Yenile  
 WCF test Istemcisi çalışırken hizmette bir değişiklik yapılırsa ve bu hizmetin WCF test Istemcisi uygulamasının güncel olduğundan emin olmak istiyorsanız, hizmetin hizmet köküne sağ tıklayın ve **hizmeti Yenile**' yi seçin. Yenilemeden sonra hizmet durumunun sıfırlandığını unutmayın.  
  
 Ara sunucu oluşturma, ikili derleme veya hizmet çağırma sırasında, bir hizmetin yenilenmesini destekleyen menü öğeleri devre dışı bırakılır. Hizmet çağrısı da devre dışı bırakılır.  
  
## <a name="location-of-files-generated-by-the-test-client"></a>Test Istemcisi tarafından oluşturulan dosyaların konumu  
 Varsayılan olarak, WCF test Istemcisi oluşturulan istemci kodunu ve yapılandırma dosyalarını "%appdata%\Local\temp\Test Istemci projeleri" klasöründe depolar. Bu klasör, WCF test Istemcisi çıktıktan sonra silinir. Bir yapılandırma dosyası WCF test Istemcisinde değiştirilirse ve **Hizmetler başlatılırken her zaman** yapılandırmayı yeniden oluştur seçeneği devre dışı bırakılmışsa, değiştirilen dosya "My Documents\mediconfig" klasörüne, eşleme Ile "My belgelerimin test istemci projeleri" altına kopyalanır ( meta veri-adres-dosya-adı) XML dosyası bir dizin olarak.  
  
 Ayrıca, WCF test istemcisini bir komut satırında başlatabilir, oluşturulan dosyaları depolamak için `/ProjectPath` istenen yeni bir yol belirtmek için anahtarını kullanabilir veya varsayılan konumu geri yüklemek için `/RestoreProjectPath` anahtarını kullanabilirsiniz. Sözdizimi aşağıdaki gibidir:  
  
 `wcfTestClient.exe /ProjectPath [desired location]`  
  
 Bu komutun çalıştırılması WCF test Istemcisi 'ni açmaz. Yalnızca klasör konumu değişir. Bu komutu, WCF test Istemcisinin çalışıp çalışmadığını, çalıştırabilirsiniz. WCF test Istemcisi yeniden başlatıldığında yeni konum uygulanır. Konum bilgileri kayıt defterine veya "%appdata%\Local\temp\Test Istemci projeleri" klasöründeki WcfTestClient. exe. Option dosyasına kaydedilebilir.  
  
## <a name="features-supported-by-wcf-test-client"></a>WCF test Istemcisi tarafından desteklenen özellikler  
 WCF test Istemcisi tarafından desteklenen özelliklerin listesi aşağıda verilmiştir:  
  
- Hizmet çağrısı: İstek/yanıt ve tek yönlü ileti.  
  
- Bağlamalar: Svcutil. exe tarafından desteklenen tüm bağlamalar.  
  
- Oturum denetleniyor.  
  
- İleti sözleşmesi.  
  
- XML serileştirme.  
  
 WCF test Istemcisi tarafından desteklenmeyen özelliklerin listesi aşağıda verilmiştir:  
  
- Türler: <xref:System.IO.Stream>, <xref:System.ServiceModel.Channels.Message> <xref:System.Xml.Serialization.IXmlSerializable> , <xref:System.Xml.XmlElement> ,<xref:System.Xml.XmlNode>,, ilişkili<xref:System.Xml.Serialization.XmlSchemaProviderAttribute> özniteliği ve ve<xref:System.Xml.Linq.XElement>türleri dahil olmak üzere arabirimi uygulayan türler <xref:System.Xml.Linq.XDocument> <xref:System.Xml.XmlAttribute> ve ADO.net <xref:System.Data.DataTable> türü.  
  
- Çift yönlü sözleşme.  
  
- İşlem.  
  
- Güven CardSpace, sertifika ve Kullanıcı adı/parola.  
  
- Lara WSFederationbinding, tüm bağlam bağlamaları ve https bağlama, WebHttpbinding (JSON yanıt iletisi desteği).  
  
## <a name="closing-wcf-test-client"></a>WCF test Istemcisi kapatılıyor  
 WCF test Istemcisini aşağıdaki yollarla kapatabilirsiniz:  
  
- **Dosya** menüsünde **Çıkış**' a tıklayın. Alternatif olarak, WCF test Istemcisi ana penceresinde **Kapat**' a tıklayın. Bu eylemlerin her ikisi de WCF hizmeti otomatik ana bilgisayarını kapatır ve WCF test Istemcisi Visual Studio tarafından başlatılmışsa Visual Studio hata ayıklama işlemini durdurur.  
  
- Bildirim alanındaki **WCF hizmeti ana bilgisayar** simgesine sağ tıklayın ve ardından çıkış ' a tıklayın **.** Bu, hem WCF hizmeti otomatik ana bilgisayarı hem de WCF test Istemcisini kapatır ve Visual Studio hata ayıklama işlemini sonlandırır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Hizmet Konağı (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)
