---
title: Dış Kural Kümesi Araç Seti
ms.date: 03/30/2017
ms.assetid: a306d283-a031-475e-aa01-9ae86e7adcb0
ms.openlocfilehash: eb59b02d469788b23126f4e02c5b7ae5a63081f0
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094676"
---
# <a name="external-ruleset-toolkit"></a>Dış Kural Kümesi Araç Seti

Normalde, kurallar bir iş akışı uygulaması içinde kullanıldığında, kurallar derlemenin bir parçasıdır. Bazı senaryolarda, RuleSets 'i derlemeden ayrı tutmak isteyebilirsiniz, böylece iş akışı derlemesini yeniden oluşturma ve dağıtma işlemi yapılmadan güncelleştirilebilirler. Bu örnek, bir veritabanında RuleSets 'i yönetmenizi ve düzenlemenizi ve çalışma zamanındaki bir iş akışından bu RuleSets 'e erişmenize olanak tanır. Bu, kural kümesi değişikliklerini otomatik olarak birleştirmek için çalışan iş akışı örneklerinin kullanılmasını sağlar.

Dış RuleSet Toolkit örneği, bir veritabanında RuleSet sürümlerini yönetmek ve düzenlemek için kullanabileceğiniz Windows Forms tabanlı bir araç içerir. Ayrıca, bu kuralları yürütmek için bir etkinlik ve bir konak hizmeti içerir.

> [!NOTE]
> Bu örnek [Microsoft SQL Server](/sql)gerektirir.

Visual Studio, Windows Workflow Foundation (WF) bir parçası olarak bir RuleSet Düzenleyicisi sağlar. Bu düzenleyiciyi bir iş akışındaki `Policy` etkinliğine çift tıklayarak başlatabilirsiniz. tanımlanan RuleSet nesnesini iş akışıyla ilişkili. Rules dosyasına seri hale getirir (bir `Policy` etkinlik iş akışında bir RuleSet örneği çalıştırır). . Rules dosyası, iş akışı projesi oluşturduğunuzda bir kaynak olarak derlemeye derlenir.

Bu örneğin bileşenleri şunlardır:

- Veritabanındaki RuleSet sürümlerini düzenlemek ve yönetmek için kullanabileceğiniz bir RuleSet grafik kullanıcı arabirimi aracı.

- Konak uygulamasında yapılandırılan ve kural kümelerine veritabanından erişen bir RuleSet hizmeti.

- RuleSet hizmetinden bir RuleSet isteyen ve RuleSet 'i iş akışı ile çalıştıran `ExternalPolicy` etkinlik.

Bileşenlerin etkileşimi aşağıdaki görüntüde gösterilmiştir. Aşağıdaki bölümlerde her bir bileşen açıklanır.

![Dış RuleSet araç seti örneğine genel bakış gösteren diyagram.](./media/external-ruleset-toolkit/ruleset-toolkit-overview.gif)

> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ExternalRuleSetToolKit`

## <a name="ruleset-tool"></a>RuleSet aracı

Aşağıdaki görüntü, RuleSet aracının bir ekran görüntüsüdür. **Kural deposu** menüsünde, kullanılabilir kural kümelerini veritabanından yükleyebilir ve değiştirilen RuleSets 'i depoya geri kaydedebilirsiniz. Bir uygulama yapılandırma dosyası RuleSet veritabanı için bir veritabanı bağlantı dizesi sağlar. Aracı başlattığınızda, kural kümelerini yapılandırılmış veritabanından otomatik olarak yükler.

![RuleSet tarayıcısını gösteren ekran görüntüsü.](./media/external-ruleset-toolkit/ruleset-browser-dialog.gif)

RuleSet Aracı, kural kümelerine büyük ve küçük sürüm numaraları uygular ve birden çok sürümü aynı anda korumanıza ve depolamanıza olanak tanır (araç, sürüm oluşturma özelliğine ek olarak hiçbir kilitleme veya diğer yapılandırma yönetimi özelliği sağlamaz). Aracı kullanarak yeni RuleSet sürümleri oluşturabilir veya var olan sürümleri silebilirsiniz. **Yeni**' ye tıkladığınızda araç yeni bir RuleSet adı oluşturur ve 1,0 sürümünü uygular. Bir sürümü kopyaladığınızda, araç, içerilen kurallar dahil olmak üzere seçili RuleSet sürümünün bir kopyasını oluşturur ve yeni, benzersiz sürüm numaraları atar. Bu sürüm numaraları, var olan RuleSets 'in sürüm numaralarına göre yapılır. Kural kümesi adını ve sürüm numaralarını formdaki ilişkili alanları kullanarak değiştirebilirsiniz.

**Kuralları Düzenle**' ye tıkladığınızda, aşağıdaki görüntüde gösterildiği gibi RuleSet Düzenleyicisi başlar:

![RuleSet düzenleyicisini gösteren ekran görüntüsü.](./media/external-ruleset-toolkit/ruleset-editor-dialog.gif)

Bu, Visual Studio eklentisinin Windows Workflow Foundation bir parçası olan Düzenleyici iletişim kutusunun yeniden barındırılması. IntelliSense desteği de dahil olmak üzere aynı işlevselliği sağlar. Kurallar, araç içindeki RuleSet ile ilişkili bir hedef türe (örneğin, bir iş akışı) göre yazılır; Ana araç iletişim kutusunda **Araştır** ' a tıkladığınızda, Şekil 4 ' te gösterildiği gibi **Iş akışı/tür Seçicisi** iletişim kutusu görüntülenir.

![İş &#47;akışı türü seçimi](./media/71f08d57-e8f2-499e-8151-ece2cbdcabfd.gif "71f08d57-e8f2-499e-8151-ece2cbdcabfd")

Şekil 4: Iş akışı/tür Seçici

Bir derlemeyi ve bu derleme içindeki belirli bir türü belirtmek için **Iş akışı/tür Seçicisi** iletişim kutusunu kullanabilirsiniz. Bu tür, kuralların yazıldığı (ve çalıştırıldığı hedef türüdür). Çoğu durumda, hedef türü bir iş akışı veya başka bir etkinlik türüdür. Ancak, herhangi bir .NET türü için bir RuleSet çalıştırabilirsiniz.

Derleme dosyasının yolu ve veritabanı `name are stored with the` RuleSet, bu sayede RuleSet veritabanından alındığında, araç otomatik olarak hedef türünü yüklemeye çalışır.

**Iş akışı/tür Seçicisi** Iletişim kutusunda **Tamam** ' a tıkladığınızda, hedef türün kuralların başvurduğu tüm üyelere sahip olduğundan emin olmak Için seçilen türü RuleSet 'e göre doğrular. Hatalar **doğrulama hataları** iletişim kutusunda gösterilir. Hatalara karşın değişikliğe devam etmeyi seçebilirsiniz veya **iptal**' e tıklayabilirsiniz. Ana araç iletişim kutusundaki **Araçlar** menüsünde, kural kümesi sürümünü hedef etkinliğe göre yeniden doğrulamak için **Doğrula** ' ya tıklayabilirsiniz.

![Doğrulama hataları iletişim kutusunu gösteren ekran görüntüsü.](./media/external-ruleset-toolkit/validation-errors-dialog.png)

Araçtaki **veri** menüsünde, RuleSets 'i içeri ve dışarı aktarabilirsiniz. **Içeri aktar**' a tıkladığınızda, bir. Rules dosyası seçebileceğiniz bir dosya Seçici iletişim kutusu görüntülenir. Bu, başlangıçta Visual Studio 'da oluşturulmuş bir dosya olabilir veya olmayabilir. . Rules dosyası bir koşul koleksiyonu ve RuleSets koleksiyonu içeren serileştirilmiş bir `RuleDefinitions` örneği içermelidir. Araç, koşullar koleksiyonunu kullanmaz, ancak Visual Studio ortamıyla etkileşime izin vermek için `RuleDefinitions`. Rules biçimini kullanır.

Bir. Rules dosyası seçildikten sonra bir **RuleSet Seçicisi** iletişim kutusu görüntülenir. İletişim kutusunu, içe aktarmak istediğiniz dosyadan RuleSets ' i seçmek için kullanabilirsiniz (varsayılan olarak tüm RuleSets 'ler belirtilir). . Rules dosyasındaki RuleSets 'in sürüm numaraları yoktur, çünkü bir WF projesi içindeki sürümleriniz derleme sürümüyle aynı. İçeri aktarma işlemi sırasında araç otomatik olarak bir sonraki kullanılabilir ana sürüm numarasını (içeri aktardıktan sonra değiştirebilirsiniz) atar; atanan sürüm numaralarını **RuleSet Seçicisi** listesinde görebilirsiniz.

İçeri aktardığı her RuleSet için araç, kural kümesinde kullanılan üyelere göre. Rules dosyasının (varsa) konumu altında bulunan bin\Debug klasöründen ilişkili türü bulmaya çalışır. Araç birden çok eşleşen tür bulursa,. Rules dosya adı ve tür adı arasındaki eşleşmeyi temel alan bir tür seçme girişiminde bulunur (örneğin, `Workflow1` türü Workflow1. Rules öğesine karşılık gelir). Birden çok eşleşme mevcutsa, türü seçmeniz istenir. Bu otomatik tanımlama mekanizması eşleşen bir derlemeyi veya türü bulamazsa, içeri aktardıktan sonra ana araç iletişim kutusunda, ilişkili türe gitmek için **Git ' e** tıklayabilirsiniz. Aşağıdaki görüntüde RuleSet Seçicisi gösterilmektedir:

![RuleSet Seçicisi iletişim kutusunu gösteren ekran görüntüsü.](./media/external-ruleset-toolkit/ruleset-selector-dialog.gif)

Ana araç menüsünden **veri-dışarı aktar** ' a tıkladığınızda, **kural kümesi Seçicisi** iletişim kutusu yeniden görünür ve bu, dışarı aktarılması gereken veritabanından RuleSets 'i belirleyebilirsiniz. **Tamam**' a tıkladığınızda, bir **dosyayı kaydet** iletişim kutusu görünür ve burada elde edilen. Rules dosyasının adını ve konumunu belirtebilirsiniz. . Rules dosyası sürüm bilgisi içermediğinden, yalnızca belirli bir RuleSet adına sahip bir RuleSet sürümü seçebilirsiniz.

## <a name="policyfromservice-activity"></a>PolicyFromService etkinliği

`PolicyFromService` etkinliğinin kodu basittir. WF ile sunulan `Policy` etkinliği çok benzer, ancak. Rules dosyasından hedef RuleSet 'i almak yerine, RuleSet örneğini almak için bir konak hizmeti çağırır. Ardından, kural kümesini kök iş akışı etkinlik örneğine göre çalıştırır.

Etkinliğini bir iş akışında kullanmak için, iş akışı projenizden `PolicyActivities` ve `RuleSetService` derlemeler için bir başvuru ekleyin. Etkinliği araç kutusuna ekleme hakkında bir tartışma için bu konunun sonundaki yordama bakın.

Etkinlik iş akışınıza yerleştirdikten sonra, çalıştırılacak RuleSet 'in adını sağlamanız gerekir. Adı bir sabit değer olarak girebilir veya başka bir etkinliğin iş akışı değişkenine veya özelliğine bağlayabilirsiniz. İsteğe bağlı olarak, çalıştırılması gereken belirli bir RuleSet için sürüm numaralarını girebilirsiniz. Birincil ve ikincil sürüm numaraları için varsayılan değer olan 0 ' ı bıraktığınızda, etkinlik için veritabanındaki en son sürüm numarası otomatik olarak sağlanır.

## <a name="ruleset-service"></a>RuleSet hizmeti

Hizmet, belirtilen RuleSet sürümünü veritabanından almaktan ve çağrı etkinliğine döndürmekten sorumludur. Daha önce anlatıldığı gibi, `GetRuleSet` çağrısında geçirilen büyük ve küçük sürüm değerlerinin ikisi de 0 ise, hizmet en son sürümü alır. Bu noktada, RuleSet tanımlarının veya örneklerinin önbelleğe alınması yoktur; benzer şekilde, kural kümesi sürümlerini, devam eden RuleSets 'ler olarak ayırt etmek için "dağıtılmış" olarak işaretlemek için bir özellik yoktur.

Hizmet tarafından erişilecek veritabanının bir uygulama yapılandırma dosyası kullanılarak konakta yapılandırılması gerekir.

#### <a name="to-run-the-tool"></a>Aracı çalıştırmak için

1. Araç ve hizmet tarafından kullanılan RuleSet tablosunu ayarlayan klasör bir Setup. SQL dosyası içerir. SQL Express üzerinde Rules veritabanını oluşturmak ve RuleSet tablosunu ayarlamak için Setup. cmd toplu iş dosyasını çalıştırabilirsiniz.

2. Toplu iş dosyasını veya Setup. SQL ' i düzenleyin ve SQL Express 'ı kullanmayı ya da tabloyu `Rules`dışında bir veritabanına yerleştirmek için, RuleSet aracında ve `UsageSample` projelerindeki uygulama yapılandırma dosyaları aynı bilgilerle düzenlenmelidir.

3. Setup. SQL betiğini çalıştırdıktan sonra, `ExternalRuleSetToolkit` çözümü oluşturabilir ve ardından ExternalRuleSetTool projesinden RuleSet aracını başlatabilirsiniz.

4. `RuleSetToolkitUsageSample` sıralı Iş akışı konsol uygulaması çözümü, örnek bir iş akışı içerir. İş akışı, hedef RuleSet 'in çalıştırıldığı `PolicyFromService` etkinlik ve iki değişkenden oluşur `orderValue` ve `discount`.

5. Örneği kullanmak için `RuleSetToolkitUsageSample` çözümü oluşturun. Ardından RuleSet aracı ana menüsünde, **veri-Içeri aktar** ' a tıklayın ve RuleSetToolkitUsageSample klasöründeki Discountrutaset. Rules dosyasına gelin. İçeri aktarılan RuleSet 'i veritabanına kaydetmek için **kural deposu-kaydet** menü seçeneğine tıklayın.

6. `PolicyActivities` derlemesine örnek iş akışı projesinden başvurulduğundan, iş akışında `PolicyFromService` etkinliği görünür. Ancak, araç kutusunda varsayılan olarak görünmez. Araç kutusuna eklemek için aşağıdakileri yapın:

    - Araç kutusuna sağ tıklayın ve **öğeleri seç** ' i seçin (Bu işlem biraz zaman alabilir).

    - **Araç kutusu öğelerini Seç** iletişim kutusu göründüğünde, **Etkinlikler** sekmesine tıklayın.

    - `ExternalRuleSetToolkit` çözümünde `PolicyActivities` derlemesine gidin ve **Aç**' a tıklayın.

    - **Araç kutusu öğelerini Seç** iletişim kutusunda `PolicyFromService` etkinliğinin seçildiğinden emin olun ve ardından **Tamam**' a tıklayın.

    - Etkinlik artık **Rulesettoolkitusagesample Components** kategorisindeki araç kutusunda görünmelidir.

7. RuleSet hizmeti, Program.cs içinde aşağıdaki deyimden yararlanarak konsol uygulama ana bilgisayarında zaten yapılandırılmış.

    ```csharp
    workflowRuntime.AddService(new RuleSetService());
    ```

8. Ayrıca, bir yapılandırma dosyası kullanarak konakta hizmeti yapılandırabilirsiniz; Ayrıntılar için SDK belgelerine bakın.

9. Hizmet tarafından kullanılacak veritabanına yönelik bağlantı dizesini belirtmek için iş akışı projesine bir uygulama yapılandırma dosyası eklenir. Bu, RuleSet aracı tarafından kural kümesi tablosunu içeren veritabanına işaret eden aynı bağlantı dizesi olmalıdır.

10. Artık `RuleSetToolkitUsageSample` projeyi diğer iş akışı konsol uygulamaları gibi çalıştırabilirsiniz. Visual Studio 'da F5 veya CTRL + F5 tuşlarına basın veya RuleSetToolkitUsageSample. exe dosyasını doğrudan çalıştırın.

    > [!NOTE]
    > Kullanım örneğini yeniden derlemek için RuleSet aracını kapatmanız gerekir, çünkü araç kullanım örneği derlemesini yükler.
