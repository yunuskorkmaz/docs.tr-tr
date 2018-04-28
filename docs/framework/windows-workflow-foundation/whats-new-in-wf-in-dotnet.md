---
title: Ne&#39;s .NET 4.5, Windows Workflow Foundation'deki yenilikler
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 195c43a8-e0a8-43d9-aead-d65a9e6751ec
caps.latest.revision: 32
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: fa529ddbdfa05ce876c99efd4a717c6136cf6686
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="what39s-new-in-windows-workflow-foundation-in-net-45"></a>Ne&#39;s .NET 4.5, Windows Workflow Foundation'deki yenilikler
Windows Workflow Foundation (WF) [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] yeni etkinlikler, Tasarımcısı özellikleri ve iş akışı geliştirme modeli gibi birçok yeni özellik sunar. Birçok, ancak tüm, sunulan yeni iş akışı özellikleri [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] yeniden barındırılan iş akışı Tasarımcısı'nda desteklenir. [!INCLUDE[crabout](../../../includes/crabout-md.md)] desteklenen, yeni özellikler bkz [Rehosted iş akışı Tasarımcısı'nda yeni iş akışı Foundation 4.5 özellikleri için destek](../../../docs/framework/windows-workflow-foundation/wf-features-in-the-rehosted-workflow-designer.md). [!INCLUDE[crabout](../../../includes/crabout-md.md)] geçirme .NET 3.0 ve en son sürümü kullanmak için .NET 3.5 iş akışı uygulamaları bkz [Geçiş Kılavuzu](../../../docs/framework/windows-workflow-foundation/migration-guidance.md). Bu konuda sunulan yeni iş akışı özelliklerine genel bakış sağlayan [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].  
  
> [!WARNING]
>  İçinde sunulan yeni Windows Workflow Foundation özellikleri [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] framework'ün önceki sürümlerini hedefleyen projeler için kullanılabilir değil. Hedefleyen bir projede varsa [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] framework'ün önceki bir sürüme çeşitli sorunlar oluşabilir yeniden yöneliktir.  
>   
>  -   C# ifadeleri değiştirilecek Tasarımcısı'nda iletiyle **değeri XAML'de ayarlandığı**.  
> -   Aşağıdaki hata dahil olmak üzere birçok derleme hataları oluşur.  
>   
>  **Dosya biçimi geçerli hedefleme framework ile uyumlu değil. Dosya biçimine dönüştürmek için lütfen açıkça dosyayı kaydedin. Dosyayı kaydedin ve tasarımcı yeniden sonra bu hata iletisini kaybolur.**  
  
##  <a name="BKMK_Versioning"></a> İş akışı sürüm oluşturma  
 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] birçok yeni sürüm oluşturma özelliği göre yeni sunulan <xref:System.Activities.WorkflowIdentity> sınıfı. <xref:System.Activities.WorkflowIdentity> İş akışı uygulama yazarları tanımına kalıcı iş akışı örneğiyle eşleme için bir mekanizma sağlar.  
  
-   Kullanan geliştiriciler <xref:System.Activities.WorkflowApplication> barındırma kullanabileceğiniz <xref:System.Activities.WorkflowIdentity> bir iş akışı yan yana birden fazla sürümünü barındırma etkinleştirmek için. Kullanarak yeni kalıcı iş akışı örnekleri yüklenebilir <xref:System.Activities.WorkflowApplicationInstance> sınıfı ve ardından <xref:System.Activities.WorkflowApplicationInstance.DefinitionIdentity%2A> iş akışı tanımı doğru sürümü başlatılırken sağlamak için ana bilgisayar tarafından kullanılan <xref:System.Activities.WorkflowApplication>. Daha fazla bilgi için bkz: [kullanarak WorkflowIdentity ve sürüm oluşturma](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md) ve [nasıl yapılır: bir iş akışı yan yana birden fazla sürümünü konak](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md).  
  
-   <xref:System.ServiceModel.WorkflowServiceHost> Çoklu sürüm konak sunulmuştur. Bir iş akışı hizmeti yeni bir sürümü dağıtıldığında, yeni örnekleri yeni hizmet kullanılarak oluşturulur, ancak önceki sürümünü kullanarak mevcut örnekleri tamamlayın. Daha fazla bilgi için bkz: [WorkflowServiceHost yan yana sürüm oluşturma](../../../docs/framework/wcf/feature-details/side-by-side-versioning-in-workflowservicehost.md).  
  
-   Dinamik güncelleştirme kalıcı iş akışı örneği tanımını güncelleştirmek için bir mekanizma sağlayan sunulmuştur. Daha fazla bilgi için bkz: [dinamik güncelleştirme](../../../docs/framework/windows-workflow-foundation/dynamic-update.md) ve [nasıl yapılır: iş akışı örneği çalışma tanım güncelleştirme](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md).  
  
-   SqlWorkflowInstanceStoreSchemaUpgrade.sql veritabanı komut dosyası kullanılarak oluşturulan Kalıcılık veritabanları yükseltmek için sağlanan [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] veritabanı komut dosyaları. Bu komut dosyası güncelleştirmeleri [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] sunulan yeni sürüm özelliklerini desteklemek için Kalıcılık veritabanlarını [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]. Veritabanında kalıcı iş akışı örnekleri varsayılan sürüm değerleri verilir ve yan yana yürütme ve dinamik güncelleştirme katılabilirsiniz. Daha fazla bilgi için bkz: [destek iş akışı sürüm oluşturma için .NET Framework 4 Kalıcılık veritabanlarını yükseltme](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases).  
  
##  <a name="BKMK_NewActivities"></a> Etkinlikler  
 Yerleşik etkinlik kitaplığı yeni etkinlikler ve varolan etkinlikleri için yeni özellikler içerir.  
  
###  <a name="BKMK_NoPersistScope"></a> NoPersist kapsam  
 <xref:System.Activities.Statements.NoPersistScope> bir iş akışı NoPersistScope'nın alt etkinlikler yürütülürken kalıcı engelleyen bir yeni kapsayıcı etkinliğidir. Bu, burada iş akışı, iş akışını dosya tanıtıcıları gibi veya veritabanı işlemleri sırasında makine özgü kaynakları kullandığında gibi kalıcı için uygun değildir senaryolarda kullanışlıdır. Daha önce Kalıcılık özel bir etkinliğin yürütme sırasında oluşmasını önlemek için <xref:System.Activities.NativeActivity> kullanılan bir <xref:System.Activities.NoPersistHandle> gerekli değildi.  
  
###  <a name="BKMK_NewFlowchartCapabilities"></a> Yeni akış özellikleri  
 Akış çizelgeleri için güncelleştirilir [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] ve aşağıdaki yeni özelliklere sahiptir:  
  
-   `DisplayName` Özelliği bir <xref:System.Activities.Statements.FlowSwitch%601> veya <xref:System.Activities.Statements.FlowDecision> etkinliktir düzenlenebilir. Bu etkinliğin amacı hakkında daha fazla bilgi göster etkinlik Tasarımcısı sağlayacaktır.  
  
-   Akış çizelgeleri adlı yeni bir özellik olan <xref:System.Activities.Statements.Flowchart.ValidateUnconnectedNodes%2A>; bu özellik için varsayılan değer `False`. Bu özellik ayarlanmışsa `True`, sonra bağlantısız akış düğümleri doğrulama hataları oluşturur.  
  
## <a name="support-for-partial-trust"></a>Kısmi güven için destek  
 İş akışlarında [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)] tam güvenilir uygulama etki alanı gerekli. İçinde [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], iş akışları, kısmi güven ortamında çalışabilir. Kısmi güven ortamında, üçüncü taraf bileşenleri konağının kaynaklara tam erişim izni olmadan kullanılabilir. Kısmi güvende çalışan iş akışları hakkında bazı sorunları aşağıdaki gibidir:  
  
1.  İçinde yer alan eski bileşenleri (kuralları dahil) kullanarak <xref:System.Activities.Statements.Interop> etkinlik altında kısmi güven desteklenmez.  
  
2.  Kısmi güvende iş akışlarını çalıştıran <xref:System.ServiceModel.WorkflowServiceHost> desteklenmiyor.  
  
3.  Kısmi güven kalıcı durumlar olası bir güvenlik tehdidi bir senaryodur. Özel durumları, bir uzantı türü kalıcı yapma devre dışı bırakmak için <xref:System.Activities.ExceptionPersistenceExtension> projeye kalıcı özel durumlar dışında opt için eklenmesi gerekir. Aşağıdaki kod örneği, bu tür gösterilmiştir.  
  
    ```  
    public class ExceptionPersistenceExtension   
    {  
        public ExceptionPersistenceExtension()   
        {   
            this.PersistExceptions = false;   
        }   
        public bool PersistExceptions { get; set; }   
    }  
    ```  
  
     Özel durumlar değil serileştirilmesi için özel durumlar içinde kullanılan olun bir <xref:System.Activities.Statements.NoPersistScope>.  
  
4.  Etkinlik yazarlar geçersiz kılma <xref:System.Activities.Activity.CacheMetadata%2A> otomatik olarak yansıma türü karşı yürütme iş akışı çalışma zamanı zorunda kalmamak için. Bağımsız değişkenler ve alt etkinlikler boş olması gerekir ve <xref:System.Activities.ActivityMetadata.Bind%2A> açıkça çağrılmalıdır. Geçersiz kılma hakkında daha fazla bilgi için <xref:System.Activities.Activity.CacheMetadata%2A>, bkz: [CacheMetadata verilerle gösterme](../../../docs/framework/windows-workflow-foundation/exposing-data-with-cachemetadata.md). Ayrıca, olan türü olan bağımsız değişkenler örneklerini `internal` veya **özel** açıkça oluşturulmalıdır <xref:System.Activities.Activity.CacheMetadata%2A> yansıma tarafından oluşturulmasını önlemek için.  
  
5.  Türlerini kullanmaz <xref:System.Runtime.Serialization.ISerializable> veya <xref:System.SerializableAttribute> seri hale getirme için; serileştirilmesi için türleri desteklemesi <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
6.  Kullanan ifadeler <xref:System.Activities.Expressions.LambdaValue%601> gerektiren <xref:System.Security.Permissions.ReflectionPermissionAttribute.RestrictedMemberAccess%2A>ve bu nedenle kısmi güven altında çalışmaz. Kullanan iş akışları <xref:System.Activities.Expressions.LambdaValue%601> ifadeleri öğesinden türetilen etkinliklerle değiştirmelisiniz <xref:System.Activities.CodeActivity%601>. biçimindeki telefon numarasıdır.  
  
7.  İfadeler kullanarak derlenemiyor <xref:System.Activities.XamlIntegration.TextExpressionCompiler> veya Visual Basic derleyici kısmi güvende barındırılan ancak önceden derlenmiş ifadeleri çalıştırılabilir.  
  
8.  Kullanan tek bir derleme [Düzey 2 saydamlık](http://aka.ms/Level2Transparency) kullanılamaz [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] tam güvende ve [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] kısmi güvende.  
  
##  <a name="BKMK_NewDesignerCapabilites"></a> Yeni Tasarımcısı özellikleri  
  
###  <a name="BKMK_DesignerSearch"></a> Tasarımcı arama  
 Daha büyük iş akışları daha kolay yönetilebilir hale getirmek için iş akışları şimdi anahtar sözcüğüyle aranabilir. Bu özellik yalnızca Visual Studio'da kullanılabilir; Bu özellik rehosted Tasarımcısı'nda kullanılamıyor. Aramaları iki tür vardır:  
  
-   İle birlikte başlatılan Hızlı Bul **Ctrl + F** veya **Düzenle**, **bulma ve değiştirme**, **Hızlı Bul'u**.  
  
-   İle birlikte başlatılan dosyalarında bulmak **Ctrl + Shift + F** veya **Düzenle**, **bulma ve değiştirme**, **dosyalarda Bul**.  
  
 Değiştir desteklenmediğini unutmayın.  
  
####  <a name="BKMK_QuickFind"></a> Hızlı Bul  
 İş akışlarında arama anahtar sözcükleri aşağıdaki Tasarımcı öğeler eşleşir:  
  
-   Özelliklerini <xref:System.Activities.Activity> nesneleri <xref:System.Activities.Statements.FlowNode> nesneleri <xref:System.Activities.Statements.State> nesneleri <xref:System.Activities.Statements.Transition> nesneleri ve diğer özel akış denetimi öğeleri.  
  
-   Değişkenler  
  
-   Arguments  
  
-   İfadeler  
  
 Hızlı Bul tasarımcının üzerinde gerçekleştirilen <xref:System.Activities.Presentation.Model.ModelItem> ağacı. Hızlı bulma iş akışı tanımı'nda içeri aktarılan ad alanları bulamaz.  
  
####  <a name="BKMK_FindInFiles"></a> Dosyalarda Bul  
 İş akışlarında arama anahtar sözcükleri iş akışı dosyalarını gerçek içeriği ile eşleşir. Arama sonuçlarını Visual Studio Bul sonuçları görünümü bölmesinde gösterilir. Sonuç öğeyi çift iş akışı Tasarımcısı'nda eşleşme içeren etkinlik gider.  
  
###  <a name="BKMK_VariableDeleteContextMenu"></a> Değişkeni ve bağımsız değişkeni Tasarımcısı'nda bağlam menüsü öğesini sil  
 İçinde [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], değişkenler ve bağımsız değişkenler yalnızca silinmesi için klavyeyi kullanma Tasarımcısı'nda. İle başlayarak [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], değişkenler ve bağımsız değişkenler bağlam menüsünü kullanarak silinebilir.  
  
 Aşağıdaki ekran görüntüsünde değişkeni ve bağımsız değişkeni Tasarımcı bağlam menüsünü gösterir.  
  
 ![Değişken bağımsız değişken Tasarımcı bağlam menüsünü](../../../docs/framework/windows-workflow-foundation/media/designercontextmenu.png "DesignerContextMenu")  
  
###  <a name="BKMK_AutoSurround"></a> Otomatik surround sırası  
 Bir iş akışı veya belirli kapsayıcı etkinlikleri bu yana (gibi <xref:System.Activities.Statements.NoPersistScope>) yalnızca bir tek gövde etkinlik içerebilir, ikinci bir etkinlik ekleme, ilk etkinlik silmek için add Geliştirici gerekli bir <xref:System.Activities.Statements.Sequence> etkinliği ve her iki etkinlikler ekleme sıralı etkinlik. İle başlayarak [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], ikinci bir etkinlik Tasarımcı yüzeyine eklerken bir `Sequence` etkinlik otomatik olarak oluşturulacak hem etkinlikleri sarmalamak için.  
  
 Aşağıdaki ekran görüntüsü gösterildiği bir `WriteLine` etkinliğinde `Body` , bir `NoPersistScope`.  
  
 ![Otomatik&#45;çevreleyen bırakma konumu](../../../docs/framework/windows-workflow-foundation/media/autosurround1.png "AutoSurround1")  
  
 Aşağıdaki ekran görüntüsü otomatik olarak oluşturulan gösterir `Sequence` etkinliğinde `Body` ikinci bir zaman `WriteLine` ilk bırakılır.  
  
 ![Sıralı etkinlik otomatik olarak oluşturulan](../../../docs/framework/windows-workflow-foundation/media/autosurround2.png "AutoSurround2")  
  
###  <a name="BKMK_PanMode"></a> Yatay kaydırma modu  
 Daha kolay büyük bir iş akışı Tasarımcısı'nda gitmek için kaydırma modu, kaydırma çubuklarını kullanın gerek yerine geliştiricinin iş akışı görünen dilimini taşımak için tıklatın ve sürükleyin izin vererek etkinleştirilebilir. PAN modunu etkinleştirmek için düğmesi Designer sağ alt köşesindeki değildir.  
  
 Aşağıdaki ekran görüntüsünde iş akışı Tasarımcısı'nı alt sağ köşesinde bulunan pan düğmesini gösterir.  
  
 ![İş Akışı Tasarımcısı'nda PAN düğmesi](../../../docs/framework/windows-workflow-foundation/media/panbutton.png "PanButton")  
  
 Orta fare düğmesini veya Ara çubuğu iş akışı Tasarımcısı'nı kaydırmak için de kullanılabilir.  
  
###  <a name="BKMK_MultiSelect"></a> Çoklu seçim  
 Birden çok etkinliği aynı anda bunları (kaydırma modu etkinleştirilmediğinde) çevresinde bir dikdörtgen sürükleyerek veya Ctrl tuşunu basılı tutarak seçilebilir ve istenen etkinlikleri tek tek tıklatın.  
  
 Birden çok etkinlik seçimin ayrıca sürüklenen ve Tasarımcısı'nda bırakılan ve bağlam menüsünü kullanarak da bulunulması.  
  
###  <a name="BKMK_DocumentOutline"></a> İş akışı öğelerinin anahat görünümü  
 Hiyerarşik iş akışları gitmek kolaylaştırmak için bir iş akışının bileşenleri bir ağaç stili anahat görünümünde gösterilir. Anahat görünümünde görüntülenen **belge anahattı** görünümü. Üstteki menüden bu görünümü açmak için seçin **Görünüm**, **diğer pencereler**, **belge anahattı**, veya Ctrl W, u tuşlarına basın Anahat görünümünde bir düğümüne tıklayarak karşılık gelen etkinlik iş akışı Tasarımcısı'nda gider ve anahat görünümü Tasarımcısı'nda seçili etkinlikler göstermek için güncelleştirilmiştir.  
  
 Aşağıdaki ekran görüntüsünde tamamlanan iş akışını [başlangıç Öğreticisi](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md) sıralı iş akışı ile anahat görünümü gösterir.  
  
 ![Anahat görünümü iş akışı Tasarımcısı'nda](../../../docs/framework/windows-workflow-foundation/media/outlineviewinworkflowdesigner.jpg "OutlineViewinWorkflowDesigner")  
  
###  <a name="BKMK_CSharpExpressions"></a> C# ifadeleri  
 Öncesinde [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], tüm ifadeleri iş akışlarında yalnızca Visual Basic'te yazılmış. İçinde [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], Visual Basic ifadeleri yalnızca Visual Basic kullanılarak oluşturulan projeleri için kullanılır. Visual C# projeleri şimdi C# ifadeler için kullanın. Tam olarak işlevsel bir C# ifade Düzenleyicisi dilbilgisi vurgulama ve IntelliSense gibi hangi özellikleri sağlanır. Visual Basic ifadeleri kullanan önceki sürümlerde oluşturulan C# projeleri iş akışı çalışmaya devam eder.  
  
 C# ifadeleri tasarım zamanında doğrulanır. C# ifadelerde hata bir kırmızı dalgalı alt çizgi ile işaretlenir.  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)] C# ifadeleri, bkz: [C# ifadeleri](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md).  
  
###  <a name="BKMK_Visibility"></a> Daha fazla denetim görünürlüğü Kabuk çubuğu ve üstbilgi öğeleri  
 Rehosted Tasarımcısı'nda bazı standart kullanıcı Arabirimi denetimlerini belirli bir iş akışı için anlamı olmayabilir ve kapalı olabilir. İçinde [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], bu özelleştirme yalnızca Tasarımcısı'nın altındaki Kabuk çubuğu tarafından desteklenir. İçinde [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], kabuk üstbilgi öğeleri Tasarımcı üstündeki görünürlüğünü ayarlayarak ayarlanabilir <xref:System.Activities.Presentation.View.DesignerView.WorkflowShellHeaderItemsVisibility%2A> uygun ile <xref:System.Activities.Presentation.View.ShellHeaderItemsVisibility> değeri.  
  
###  <a name="BKMK_AutoConnect"></a> Otomatik olarak bağlanabilir ve akış çizelgesi ve durum makinesinin iş akışlarında otomatik ekleme  
 İçinde [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], akış iş akışında düğümler arasındaki bağlantıların el ile eklenmesi gerekiyordu. İçinde [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], akış ve Durum makinesi düğümünüz bir etkinlik araç kutusunu tasarımcı yüzeyine sürüklendiğinde görünür hale gelmiştir noktalarını otomatik olarak bağlanabilir. Bir etkinlik bu noktalarının birini otomatik olarak bırakarak gerekli bağlantı birlikte etkinlik ekler.  
  
 Aşağıdaki ekran görüntüsünde bir etkinlik Araç Kutusu'ndan sürüklendiğinde görünür hale gelmiştir ek noktalarını gösterir.  
  
 ![Otomatik bağlanma noktalarını gösteren akış çizelgesi başlangıç düğümü](../../../docs/framework/windows-workflow-foundation/media/autoconnect1.png "Autoconnect1")  
  
 Akış Çizelgesi düğümleri ve otomatik-iki düğüm arasında düğüm eklemek üzere durumları arasında etkinlikleri de bağlantıları sürüklenebilir. Aşağıdaki ekran görüntüsünde vurgulanan bağlanan satırı burada etkinlikler kullanılabilir Araç Kutusu'ndan sürüklenen ve bırakılan gösterir.  
  
 ![Otomatik&#45;etkinlikleri bırakarak için tanıtıcı Ekle](../../../docs/framework/windows-workflow-foundation/media/autoinsert.png "Autoinsert")  
  
###  <a name="BKMK_Annotations"></a> Tasarımcı ek açıklamaları  
 Büyük iş akışları geliştirmeyi kolaylaştırmak için tasarımcı tasarım işlemini izlemenize yardımcı olmak için ekleme ek açıklamaları destekler. Ek açıklama etkinlikleri, durumları, akış çizelgesi düğümleri, değişkenler ve bağımsız değişkenler eklenebilir. Aşağıdaki ekran görüntüsünde Designer'a ek açıklamaları eklemek için kullanılan bağlam menüsünü gösterir.  
  
 ![Ek açıklama bağlam menüsü](../../../docs/framework/windows-workflow-foundation/media/annotationdialog.png "annotationdialog")  
  
### <a name="debugging-states"></a>Hata ayıklama durumları  
 İçinde [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], etkinlik dışı öğeleri desteklemediği hata ayıklama kesme noktalarına yürütme birimleri değildi beri. Bu sürüm için kesme noktaları eklemek için bir mekanizma sağlar <xref:System.Activities.Statements.State> nesneleri. Üzerinde bir kesme noktası ayarlandığında bir <xref:System.Activities.Statements.State>, yürütme durumu için geçirildiğinde bozar, önce girdisini etkinlikleri veya tetikleyicileri zamanlanır.  
  
###  <a name="BKMK_ActivityDelegates"></a> Tanımlama ve ActivityDelegate nesneleri Tasarımcısı'nda kullanma  
 Etkinlikler [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] kullanılan <xref:System.Activities.ActivityDelegate> burada iş akışını diğer bölümleri ile bir iş akışının yürütme destekliyordu, ancak bu yürütme noktaları genellikle kullanarak gerekli eşit miktarda kod yürütme noktalarını göstermek için nesneleri. Bu sürümde, geliştiricilerin tanımlayabilir ve iş akışı Tasarımcısı'nı kullanarak etkinlik temsilcileri kullanabilir. Daha fazla bilgi için bkz: [nasıl yapılır: tanımlama ve iş akışı Tasarımcısı'nda aktivite temsilcileri kullanma](/visualstudio/workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer).  
  
###  <a name="BKMK_BuildTimeValidation"></a> Derleme zamanı doğrulama  
 İçinde [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], iş akışı doğrulama hataları derleme hataları bir iş akışı projesinde derleme sırasında sayılan doğru. Bu, bir iş akışı derleme geliyordu bile iş akışı doğrulama hataları zamanki proje başarılı. İçinde [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], iş akışı doğrulama hatalara yapılandırmanın başarısız olmasına neden olabilir.  
  
###  <a name="BKMK_DesignTimeValidation"></a> Tasarım zamanı arka plan doğrulama  
 İçinde [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], iş akışları kullanıcı arabirimini karmaşık ya da zaman alıcı doğrulama işlemi sırasında potansiyel olarak askıda kalabilir ön plan işlemi olarak doğrulandı. Böylece kullanıcı arabirimini engellenmez iş akışı doğrulama şimdi bir arka plan iş parçacığı üzerinde gerçekleşir.  
  
###  <a name="BKMK_ViewState"></a> XAML dosyaları ayrı bir konumda bulunan görünüm durumu  
 İçinde [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], Görünüm durumu bilgisini bir iş akışı için birçok farklı konumlarda XAML dosyası üzerinde depolanır. XAML doğrudan okuma ya da Görünüm durumu bilgileri kaldırmak için kod yazma isteyen geliştiriciler için kullanışsız budur. İçinde [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], Görünüm durumu bilgisini XAML dosyasındaki XAML dosyası içinde ayrı bir öğe olarak serileştirilmiş.  Kolayca geliştiriciler bulun ve bir etkinlik görünüm durumu bilgilerini düzenleyin veya Görünüm durumu tamamen kaldırın.  
  
###  <a name="BKMK_ExpressionExtensibility"></a> İfade genişletilebilirliği  
 İçinde [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], geliştiricilerin kendi ifade ve ifade yazma iş akışı Tasarımcısı'na takılı deneyimi oluşturmak bir yol sağlıyoruz.  
  
###  <a name="BKMK_BackwardCompatRehostedDesigner"></a> İş akışı 4.5 özellikleri rehosted Tasarımcısı'nda kabulü  
 Geriye dönük uyumluluğu korumak için bazı yeni özellikler dahil [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] rehosted Tasarımcısı'nda varsayılan olarak etkin değildir. Bu rehosted Tasarımcısı'nı kullanan mevcut uygulamaları en son sürüme güncelleştirerek ayrılır değil olduğundan emin olmaktır. Rehosted Tasarımcısı'nda yeni özellikleri etkinleştirmek için ya da ayarlamak <xref:System.Activities.Presentation.DesignerConfigurationService.TargetFrameworkName%2A> ".NET Framework 4.5" ya da kümesi tek tek üyeleri <xref:System.Activities.Presentation.DesignerConfigurationService> tek tek özellikleri etkinleştirmek için.  
  
##  <a name="BKMK_NewWFModels"></a> Yeni iş akışı geliştirme modelleri  
 Akış Çizelgesi ve sıralı iş akışı geliştirme modelleri ek olarak, bu sürüm durum makinesinin iş akışları ve sözleşme ilk iş akışı hizmetleri içerir.  
  
###  <a name="BKMK_StateMachine"></a> Durum makinesi iş akışları  
 Durum makinesi iş akışları, .NET Framework 4, sürüm 4.0.1 bir parçası olarak sunulmuştu [Microsoft .NET Framework 4 Platform Güncelleştirmesi 1](http://go.microsoft.com/fwlink/?LinkID=215092). Bu, birkaç yeni sınıflar ve Durum makinesi iş akışları oluşturmak geliştiriciler izin etkinlikler güncelleştirmenin. Bu sınıf ve etkinlikler için güncelleştirilmiş [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]. Güncelleştirmeler şunları içerir:  
  
1.  Kesme noktaları durumlarına ayarlama özelliği  
  
2.  Geçişler iş akışı Tasarımcısı'nda kopyalayıp olanağı  
  
3.  Paylaşılan tetikleyici geçiş oluşturma için tasarımcı desteği  
  
4.  Durum makinesinin iş akışları dahil olmak üzere, oluşturmak için kullanılan etkinliklerin: <xref:System.Activities.Statements.StateMachine>, <xref:System.Activities.Statements.State>, ve <xref:System.Activities.Statements.Transition>  
  
 Aşağıdaki ekran görüntüsünde tamamlanan durumu makine akışından gösterir [başlangıç Öğreticisi](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md) adım [nasıl yapılır: bir Durum makinesi iş akışı oluşturma](../../../docs/framework/windows-workflow-foundation/how-to-create-a-state-machine-workflow.md).  
  
 ![Durum makinesi iş akışı tamamlandı](../../../docs/framework/windows-workflow-foundation/media/wfstatemachinegettingstartedtutorialcomplete.JPG "WFStateMachineGettingStartedTutorialComplete")  
  
 Durum makinesi iş akışları oluşturma hakkında daha fazla bilgi için bkz: [durumu makine iş akışları](../../../docs/framework/windows-workflow-foundation/state-machine-workflows.md).  
  
###  <a name="BKMK_ContractFirst"></a> Önce anlaşma iş akışı geliştirme  
 Önce anlaşma iş akışı geliştirme aracı, kod sözleşmede ilk tasarım sonra Visual Studio birkaç tıklama ile her işlemi temsil eden araç kutusu otomatik olarak bir etkinlik şablonu oluşturmak, geliştirici sağlar. Bu etkinlikler, ardından anlaşma tarafından tanımlanan işlemleri uygulayan bir iş akışı oluşturmak için kullanılır. İş Akışı Tasarımcısı'nı bu işlemler uygulanır ve iş akışının imza sözleşme imza eşleşen emin olmak için iş akışı hizmeti doğrular. Geliştirici, ayrıca bir iş akışı hizmeti uygulanan sözleşmeleri koleksiyonu ile ilişkilendirebilirsiniz. Önce anlaşma iş akışı hizmeti geliştirme hakkında daha fazla bilgi için bkz: [nasıl yapılır: varolan bir hizmet sözleşmesini tüketen bir iş akışı hizmeti oluşturma](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md).
