---
title: Dış Kural Kümesi Araç Seti
ms.date: 03/30/2017
ms.assetid: a306d283-a031-475e-aa01-9ae86e7adcb0
ms.openlocfilehash: c453c6137beeae8eee0e356734a1f9cdf8d8568b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62005491"
---
# <a name="external-ruleset-toolkit"></a>Dış Kural Kümesi Araç Seti

Bir iş akışı uygulama içinde kuralları kullanıldığında, normal derlemenin parçası kurallardır. Bazı senaryolarda, yeniden oluşturma ve iş akışı derleme dağıtılmadan güncelleştirilebilir ayrı olarak derlemesinden RuleSets sağlamak isteyebilirsiniz. Bu örnek ve bir veritabanında RuleSets düzenleyin ve çalışma zamanında bir iş akışından bu RuleSets erişimi yönetmesine olanak tanır. Bu kural kümesi değişiklikleri otomatik olarak birleştirmek çalışan iş akışı örnekleri sağlar.

Dış kural kümesi Araç Seti örnek yönetmek ve veritabanındaki RuleSet sürümlerini düzenlemek için kullanabileceğiniz bir Windows Forms tabanlı bir araç içerir. Ayrıca, etkinlik ve bu kurallar yürütmeye yönelik bir ana bilgisayar hizmeti de içerir.

> [!NOTE]
> Bu örnek gerektirir [Microsoft SQL Server](https://go.microsoft.com/fwlink/?LinkId=96181).

Visual Studio, Windows Workflow Foundation (WF) bir parçası olarak bir kural kümesi Düzenleyicisi sağlar. Bu Düzenleyici'yi tıklatarak başlatabilirsiniz `Policy` etkinliğini bir iş akışında; iş akışıyla ilişkilendirilmiş .rules dosya için tanımlı RuleSet nesnesi seri hale getirir (bir `Policy` karşı iş akışı etkinlik çalıştırmalarını bir kural kümesi örneği). İş akışı projesi oluşturma sırasında .rules dosyanın derleme kaynağı olarak derlenir.

Bu örnek Ekle bileşenlerinin:

- Düzenleme ve veritabanındaki RuleSet sürümlerini yönetmek için kullanabileceğiniz bir RuleSet grafik kullanıcı arabirimi aracıdır.

- Ana bilgisayar uygulaması üzerinde yapılandırıldığı ve veritabanından RuleSets erişen bir RuleSet hizmeti.

- Bir `ExternalPolicy` RuleSet hizmetinden bir RuleSet istekleri ve RuleSet karşı iş akışını çalıştıran etkinlik.

Aşağıdaki görüntüde bileşenleri etkileşimi gösterilmektedir. Aşağıdaki bölümlerde, her bir bileşeni açıklar.

![Dış kural kümesi Araç Seti örneğine genel bakış gösteren diyagram.](./media/external-ruleset-toolkit/ruleset-toolkit-overview.gif)

> [!IMPORTANT]
> Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ExternalRuleSetToolKit`

## <a name="ruleset-tool"></a>Kural kümesi araç

RuleSet aracının ekran görüntüsüdür. Gelen **kural Store** menüsünde kullanılabilir RuleSets veritabanından yükleyin ve değiştirilen RuleSets depoya kaydedin. Uygulama yapılandırma dosyası bir veritabanı bağlantı dizesi için RuleSet veritabanı sağlar. Aracı'nı başlattığınızda, yapılandırılmış veritabanından otomatik olarak RuleSets yükler.

![RuleSet tarayıcı gösteren ekran görüntüsü.](./media/external-ruleset-toolkit/ruleset-browser-dialog.gif)

Kural kümesi araç aynı anda korumak ve (araç kilitleme veya diğer yapılandırma sürümü oluşturma yeteneğine ek yönetim özellikleri sağlar) birden çok sürümlerini depolamanıza olanak tanıyan RuleSets büyük ve küçük sürüm numaralarına uygular. Aracı'nı kullanarak yeni RuleSet sürümler oluşturabilir veya mevcut sürümleri silin. Tıkladığınızda **yeni**, aracı yeni bir kural kümesi adı oluşturur ve sürüm 1.0 için geçerlidir. Bir sürüm kopyaladığınızda, aracın kapsanan kuralları dahil olmak üzere seçili RuleSet sürümünün bir kopyasını oluşturur ve yeni, benzersiz sürüm numaraları atar. Bu sürüm numaralarını üzerinde mevcut RuleSets sürüm numaralarını temel alır. Formda ilişkili alanlarını kullanarak RuleSet adını ve sürüm numaralarını değiştirebilirsiniz.

Tıkladığınızda **kurallarını Düzenle**, kural kümesi Düzenleyicisi'ni başlatır, aşağıdaki görüntüde gösterildiği gibi:

![Kural kümesi Düzenleyici gösteren ekran görüntüsü.](./media/external-ruleset-toolkit/ruleset-editor-dialog.gif)

Bir Windows Workflow Foundation için Visual Studio eklentisinin bir parçası olan Düzenleyicisi iletişim yeniden barındırma budur. Bu, IntelliSense desteği dahil olmak üzere aynı işlevselliği sağlar. Kurallar, araç kümesinde ile ilişkili olan bir hedef türü (örneğin, bir iş akışı) karşı yazılan; tıkladığınızda **Gözat** ana aracı iletişim kutusunda **türündeki iş akışı Seçici** Şekil 4'te gösterildiği gibi iletişim kutusu görünür.

![İş akışı &#47;yazın seçimi](./media/71f08d57-e8f2-499e-8151-ece2cbdcabfd.gif "71f08d57-e8f2-499e-8151-ece2cbdcabfd")

Şekil 4: İş akışı/türü Seçici

Kullanabileceğiniz **türündeki iş akışı Seçici** iletişim bir derleme ve bu derleme içinde belirli bir tür belirtmek için. Hedef türü karşı kuralları yazılan (çalıştırmanız ve) türüdür. Çoğu durumda, bir iş akışı veya başka bir etkinlik türü hedef türü olur. Ancak, bir RuleSet herhangi bir .NET türü karşı çalıştırabilirsiniz.

Derleme dosya ve tür yolu `name are stored with the` RuleSet veritabanındaki zaman RuleSet veritabanından alınır böylece aracı çalışır hedef türü otomatik olarak yüklenecek.

Tıkladığınızda **Tamam** içinde **türündeki iş akışı Seçici** iletişim kutusunda, seçili türü hedef türü kurallar tarafından başvurulan tüm üyeleri olduğundan emin olmak için RuleSet karşı doğrular. Hatalar gösterilir bir **doğrulama hatalarını** iletişim. Hataları rağmen değişiklik ile devam edin veya seçebileceğiniz **iptal**. Gelen **Araçları** menüsünde ana aracı iletişim kutusunda, tıklayabilirsiniz **doğrulama** hedef etkinlik karşı RuleSet sürümü yeniden doğrulamak için.

![Doğrulama hataları iletişim kutusunu gösteren ekran görüntüsü.](./media/external-ruleset-toolkit/validation-errors-dialog.png)

Gelen **veri** menü aracında içeri ve dışarı aktarma RuleSets. Tıkladığınızda **alma**, bir dosya Seçici iletişim kutusu görünürse, .rules dosya seçin. Bu olabilir veya başlangıçta Visual Studio'da oluşturulan bir dosya olabilir. .Rules dosya seri hale getirilmiş bir içermelidir `RuleDefinitions` koşulların koleksiyonunu ve RuleSets koleksiyonunu içeren örneği. Koşulları koleksiyonu Aracı'nı kullanmaz, ancak kullanmak `RuleDefinitions` Visual Studio ortamını etkileşime izin vermek için .rules biçimi.

.Rules dosyayı seçtikten sonra bir **RuleSet Seçici** iletişim kutusu görüntülenir. İletişim kutusu içeri aktarmak istediğiniz dosyasından RuleSets seçmek için kullanabilirsiniz (varsayılan, tüm RuleSets belirtir). WF projedeki kendi sürüm oluşturma derlemenin sürümü ile aynı olduğundan RuleSets .rules dosyasında sürüm numaralarının yok. İçeri aktarma işlemi sırasında Aracı'nı (içeri aktardıktan sonra değiştirebilirsiniz) sonraki kullanılabilir ana sürüm numarası otomatik olarak atar; atanan sürüm numaraları gördüğünüz **RuleSet Seçici** listesi.

Bunu aktarır her kural kümesi için aracı denemeleri .rules dosyasının (varsa) konumu altında bin\Debug klasöründen ilişkili türünü bulun temel kümesinde kullanılan üyeler. Aracın birden çok eşleşen türleri bulur .rules dosya adı ve tür adı arasında bir eşleşme göre bir türü seçmek çalışır (örneğin, `Workflow1` Workflow1.rules için karşılık gelen türü). Birden çok eşleşme varsa, türü seçmek için istenir. Eşleşen bir derleme veya tür bulmak bu otomatik kimlik mekanizması başarısız durumunda tıklayabilirsiniz içeri aktardıktan sonra **Gözat** ilişkili türe gitmek için ana aracı iletişim. Aşağıdaki görüntüde RuleSet Seçici gösterilmektedir:

![Kural kümesi Seçici iletişim kutusunu gösteren ekran görüntüsü.](./media/external-ruleset-toolkit/ruleset-selector-dialog.gif)

Tıkladığınızda **verileri dışarı aktarma** ana aracı menüsünden **RuleSet Seçici** verilmeli veritabanından RuleSets belirlemek iletişim yeniden görünür. Tıkladığınızda **Tamam**, **dosyayı Kaydet** iletişim kutusu açılır, sonuçta elde edilen .rules dosyasının konumunu ve adını belirtebilirsiniz. .Rules dosya sürüm bilgisi içermediğinden, yalnızca belirli bir RuleSet ada sahip bir kural kümesi sürümü seçebilirsiniz.

## <a name="policyfromservice-activity"></a>PolicyFromService etkinliği

Kodu `PolicyFromService` etkinliktir basit. Gibi çalıştığını `Policy` sağlanan ile WF etkinliği, ancak ' % s'hedef RuleSet .rules dosyasından almak yerine RuleSet örneği elde etmek için bir ana bilgisayar hizmeti çağırır. Ardından RuleSet kök iş akışı etkinliği örneği karşı çalışır.

Bir iş akışında etkinlik kullanmak için bir başvuru ekleyin. `PolicyActivities` ve `RuleSetService` iş akışı projenizden derlemeler. Araç kutusuna etkinlik ekleme hakkında ayrıntılı bilgi için bu konunun sonunda yordamına bakın.

Etkinlik akışınızdaki yerleştirildikten sonra çalıştırılacak RuleSet adını sağlamanız gerekir. Değişmez değer adını girin veya bir iş akışı değişkeninin veya başka bir etkinliğin özelliği için bağlama. İsteğe bağlı olarak çalıştırılması gereken özel kural kümesi için sürüm numaraları girebilirsiniz. Birincil ve ikincil sürüm numaraları 0 varsayılan değerini değiştirmeden bırakırsanız, veritabanındaki en son sürüm numarasını etkinliği için otomatik olarak sağlanır.

## <a name="ruleset-service"></a>Kural kümesi hizmeti

Hizmet, veritabanından belirtilen kural kümesi sürümü alma ve arama etkinliğine döndürmeden sorumludur. Birincil ve ikincil sürüm değer iletilmezse daha önce açıklandığı gibi `GetRuleSet` çağrı, her iki 0 hizmetin en son sürümünü alır. Bu noktada, yoktur RuleSet tanımları veya örnekleri önbelleğe alma; benzer şekilde, RuleSet sürümleri "Sürüyor RuleSets ayrılmaları için dağıtılan" olarak işaretlemek için herhangi bir özellik vardır.

Veritabanı Hizmet tarafından erişilecek bir uygulama yapılandırma dosyası kullanarak konakta yapılandırılması gerekir.

#### <a name="to-run-the-tool"></a>Aracı çalıştırmak için

1. Araç ve hizmet tarafından kullanılan RuleSet tablo ayarlar klasörü Setup.sql dosyası içerir. SQL Express kuralları veritabanını oluşturmak için ve RuleSet tablosu oluşturmak için Setup.cmd toplu iş dosyasını çalıştırabilirsiniz.

2. Toplu iş dosyası veya Setup.sql düzenleyip SQL Express kullanmayacak şekilde veya başka bir şey adlı bir veritabanında tablo yerleştirmek için belirtin `Rules`, uygulama yapılandırma dosyaları RuleSet aracında ve `UsageSample` projeleri düzenlenmesi gerekir ile aynı bilgiler.

3. Setup.sql betiği çalıştırdıktan sonra oluşturabileceğiniz `ExternalRuleSetToolkit` çözüm ve ardından başlatma RuleSet ExternalRuleSetTool projeden aracı.

4. `RuleSetToolkitUsageSample` Sıralı iş akışı konsol uygulaması çözümü bir örnek iş akışı içerir. İş akışı oluşan bir `PolicyFromService` etkinliği ve iki değişken `orderValue` ve `discount`, ' % s'hedef RuleSet çalıştığı karşı.

5. Örneği kullanmak için yapı `RuleSetToolkitUsageSample` çözüm. RuleSet aracı ana menüden ardından **veri içeri aktarma** ve RuleSetToolkitUsageSample klasördeki DiscountRuleSet.rules dosyasına işaret. Tıklayın **kural Store tasarrufu** içeri aktarılan RuleSet veritabanına kaydetmek için menü seçeneği.

6. Çünkü `PolicyActivities` derleme örnek iş akışı projeden başvurulan `PolicyFromService` etkinlik iş akışında görünür. Bu ancak araç kutusunda varsayılan olarak görünmez. Araç kutusuna eklemek için aşağıdakileri yapın:

    - Araç kutusu sağ tıklayıp **öğelerini Seç** (Bu işlem biraz sürebilir).

    - Zaman **araç kutusu öğelerini Seç** iletişim kutusu görüntülendikten sonra **etkinlikleri** sekmesi.

    - Gözat `PolicyActivities` derlemede `ExternalRuleSetToolkit` çözüm ve tıklatın **açık**.

    - Emin `PolicyFromService` etkinlik seçili **araç kutusu öğelerini Seç** iletişim ve ardından **Tamam**.

    - Etkinlik artık araç kutusundan gözükeceğini **RuleSetToolkitUsageSample bileşenleri** kategorisi.

7. Kural kümesi hizmeti aşağıdaki deyimi Program.cs içinde kullanarak konsol uygulama konağı üzerinde zaten yapılandırılmış.

    ```csharp
    workflowRuntime.AddService(new RuleSetService());
    ```

8. Ayrıca hizmet yapılandırma dosyası kullanarak konakta yapılandırabilirsiniz; Ayrıntılar için SDK belgelerine bakın.

9. Uygulama yapılandırma dosyası, hizmet tarafından kullanılmak üzere veritabanı için bağlantı dizesini belirtmek için iş akışı projesine eklenir. Bu kural kümesi tablo içeren bir veritabanına işaret eden RuleSet aracı tarafından kullanılan aynı bağlantı dizesi olmalıdır.

10. Şimdi Çalıştır `RuleSetToolkitUsageSample` proje başka bir iş akışı konsol uygulaması gibi. F5 veya Visual Studio içinde Ctrl + F5 tuşlarına basın veya doğrudan RuleSetToolkitUsageSample.exe dosyasını çalıştırın.

    > [!NOTE]
    > Kullanım örneği derleme yüklediğinden, araç kullanım örneği derleyin RuleSet aracını kapatmanız gerekir.
