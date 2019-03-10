---
title: .NET 4.5 içinde Windows Workflow Foundation'daki yenilikler
ms.date: 03/30/2017
ms.assetid: 195c43a8-e0a8-43d9-aead-d65a9e6751ec
ms.openlocfilehash: a76ec56cf6ac5260f00031bc815b32b1e10804a4
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57718928"
---
# <a name="whats-new-in-windows-workflow-foundation-in-net-45"></a>.NET 4.5 içinde Windows Workflow Foundation'daki yenilikler

Windows Workflow Foundation (WF) [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] yeni etkinlikler, Tasarımcı özellikleri ve iş akışı geliştirme modelleri gibi birçok yeni özellik sunar. Çok sayıda, ancak tüm, sunulan yeni iş akışı özellikleri [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] yeniden barındırılan iş akışı Tasarımcısı'nda desteklenir. Desteklenen yeni özellikler hakkında daha fazla bilgi için bkz. [yeniden barındırılan iş akışı tasarımcısında yeni Workflow Foundation 4.5 özellikleri desteği](wf-features-in-the-rehosted-workflow-designer.md). En son sürümü kullanmak için .NET 3.0 ve .NET 3.5 iş akışı uygulamalarını geçirme hakkında daha fazla bilgi için bkz. [geçiş kılavuzuna](migration-guidance.md). Bu konu başlığı altında tanıtılan yeni iş akışı özelliklerine genel bakış sağlar [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].

> [!WARNING]
> Eklenen yeni Windows Workflow Foundation özellikleri [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] framework'ün önceki sürümlerini hedefleyen projeler için kullanılabilir değil. Hedefleyen bir proje varsa [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] framework'ün önceki bir sürüme çeşitli sorunlar ortaya çıkabilir yeniden yöneliktir.
>
> - C# ifadelerini değiştirilecek Tasarımcısı'nda iletinin **değer XAML ayarlandığı**.
> - Aşağıdaki hata da dahil olmak üzere çok sayıda derleme hataları oluşur.
>
> **Dosya biçimi geçerli hedefleme çerçevesi ile uyumlu değil. Dosya biçimini dönüştürmek için lütfen açıkça dosyayı kaydedin. Dosyayı kaydedin ve tasarımcıyı yeniden sonra bu hata iletisini kaybolur.**

## <a name="BKMK_Versioning"></a> İş akışı sürümü oluşturma

[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Yeni tabanlı birçok yeni sürüm oluşturma özelliği sunulan <xref:System.Activities.WorkflowIdentity> sınıfı. <xref:System.Activities.WorkflowIdentity> uygulama yazarları iş akışı tanımını kalıcı iş akışı örneğiyle eşleme için bir mekanizma sağlar.

- Kullanan geliştiriciler <xref:System.Activities.WorkflowApplication> barındırma kullanabileceğiniz <xref:System.Activities.WorkflowIdentity> birden çok sürümünü bir iş akışı yan yana barındırma olanağı. Kalıcı iş akışı örnekleri kullanarak yeni yüklenebilir <xref:System.Activities.WorkflowApplicationInstance> sınıfı ve ardından <xref:System.Activities.WorkflowApplicationInstance.DefinitionIdentity%2A> örneklerken iş akışı tanımı doğru sürümünü sağlamak için ana bilgisayar tarafından kullanılan <xref:System.Activities.WorkflowApplication>. Daha fazla bilgi için [Workflowıdentity kullanma ve sürüm oluşturma](using-workflowidentity-and-versioning.md) ve [nasıl yapılır: Bir iş akışı yan yana birden çok sürümünü konak](how-to-host-multiple-versions-of-a-workflow-side-by-side.md).

- <xref:System.ServiceModel.WorkflowServiceHost> artık bir çok sürümlü ana bilgisayardır. Bir iş akışı hizmeti yeni bir sürümü dağıtıldığında, yeni hizmetini kullanarak yeni örnekleri oluşturulur, ancak önceki sürümünü kullanarak mevcut örneklerdeki tamamlayın. Daha fazla bilgi için [WorkflowServiceHost yan yana sürüm oluşturma](../wcf/feature-details/side-by-side-versioning-in-workflowservicehost.md).

- Dinamik güncelleştirme bir kalıcı iş akışı örneğinin tanımını güncelleştirmeye yönelik bir mekanizma sağlayan kullanıma sunulmuştur. Daha fazla bilgi için [dinamik güncelleştirme](dynamic-update.md) ve [nasıl yapılır: Bir çalışan iş akışı örneğinin tanımını güncelleştirme](how-to-update-the-definition-of-a-running-workflow-instance.md).

- SqlWorkflowInstanceStoreSchemaUpgrade.sql veritabanı betiği kullanılarak oluşturulan Kalıcılık veritabanları yükseltmek için sağlanan [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] veritabanı komut dosyaları. Bu betik güncelleştirmeleri [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] de kullanıma sunulan yeni sürüm oluşturma özellikleri desteklemek için Kalıcılık veritabanlarını [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]. Veritabanında kalıcı iş akışı örnekleri varsayılan sürüm değerleri verilir ve yan yana yürütme ve dinamik güncelleştirme katılabilir. Daha fazla bilgi için [destek iş akışı sürüm oluşturma için .NET Framework 4 Kalıcılık veritabanı yükseltme](using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases).

## <a name="BKMK_NewActivities"></a> Etkinlikleri

Yerleşik etkinlik kitaplığı yeni etkinlikler ve mevcut etkinlikler için yeni özellikler içerir.

### <a name="BKMK_NoPersistScope"></a> NoPersist kapsamı

<xref:System.Activities.Statements.NoPersistScope> NoPersistScope'nın alt etkinlik yürütülürken kalıcı bir iş akışı önleyen yeni bir kapsayıcı etkinliği seçilir. Bu, burada, iş akışı, dosya tanıtıcıları gibi veya veritabanı işlemleri sırasında makine özgü kaynakları kullanan gibi sürdürülecek iş akışı için uygun değildir senaryolarda kullanışlıdır. Daha önce Kalıcılık özel bir etkinlik yürütme sırasında oluşmasını önlemek için <xref:System.Activities.NativeActivity> kullanılan bir <xref:System.Activities.NoPersistHandle> gerekiyordu.

### <a name="BKMK_NewFlowchartCapabilities"></a> Yeni akış özellikleri

Akış çizelgeleri için güncelleştirilmiş [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] ve aşağıdaki yeni özelliklere sahiptir:

- `DisplayName` Özelliği bir <xref:System.Activities.Statements.FlowSwitch%601> veya <xref:System.Activities.Statements.FlowDecision> etkinliktir düzenlenebilir. Bu etkinliğin amacı hakkında daha fazla bilgi göster etkinlik Tasarımcısı sağlar.

- Akış çizelgeleri adlı yeni bir özellik vardır <xref:System.Activities.Statements.Flowchart.ValidateUnconnectedNodes%2A>; bu özellik için varsayılan değer `False`. Bu özellik ayarlanırsa `True`, sonra bağlantısız akış düğümleri doğrulama hataları oluşturur.

## <a name="support-for-partial-trust"></a>Kısmi güven için destek

İş akışlarında [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)] tam olarak güvenilen bir uygulama etki alanı gerekli. İçinde [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], iş akışları, kısmi güven ortamında çalışabilir. Kısmi güven ortamında, konağın kaynaklara tam erişim izni olmadan üçüncü taraflara ait bileşenleri kullanılabilir. Kısmi güvende çalışan iş akışları hakkında bazı sorunlar aşağıdaki gibidir:

1. Eski bileşenleri (kuralları dahil olmak üzere) içindeki kullanarak <xref:System.Activities.Statements.Interop> etkinlik, kısmi güven altında desteklenmiyor.

2. İş akışları kısmi güvende çalışan <xref:System.ServiceModel.WorkflowServiceHost> desteklenmiyor.

3. Kısmi güven kalıcı durumlar olası bir güvenlik tehdidi bir senaryodur. Özel durumları, bir uzantı türü kalıcı yapma devre dışı bırakmak için <xref:System.Activities.ExceptionPersistenceExtension> kalıcı özel durumlar dışında iyileştirilmiş için projeye eklenmesi gerekir. Aşağıdaki kod örneği, bu tür gösterilmiştir.

    ```csharp
    public class ExceptionPersistenceExtension
    {
        public ExceptionPersistenceExtension()
        {
            this.PersistExceptions = false;
        }
        public bool PersistExceptions { get; set; }
    }
    ```

     Özel durumları değil serileştirilecek varsa, özel durumlar içinde kullanıldığından emin olun. bir <xref:System.Activities.Statements.NoPersistScope>.

4. Etkinlik yazarlar geçersiz kılmalıdır <xref:System.Activities.Activity.CacheMetadata%2A> otomatik olarak yansıma türü karşı yürütme iş akışı çalışma zamanı olmamasına özen gösterin. Bağımsız değişkenler ve alt etkinlikleri null olmayan, olmalıdır ve <xref:System.Activities.ActivityMetadata.Bind%2A> özel olarak çağrılması gerekir. Geçersiz kılma hakkında daha fazla bilgi için <xref:System.Activities.Activity.CacheMetadata%2A>, bkz: [CacheMetadata ile verileri kullanıma sunduğundan](exposing-data-with-cachemetadata.md). Ayrıca, bir türü olan bağımsız değişkenler örneklerini `internal` veya **özel** açıkça oluşturulmalıdır <xref:System.Activities.Activity.CacheMetadata%2A> yansıma tarafından oluşturulmasını önlemek için.

5. Türlerini kullanmaz <xref:System.Runtime.Serialization.ISerializable> veya <xref:System.SerializableAttribute> serileştirilecek türlere serileştirme için; desteklemelidir <xref:System.Runtime.Serialization.DataContractSerializer>.

6. Kullanan ifadelerde <xref:System.Activities.Expressions.LambdaValue%601> gerektiren <xref:System.Security.Permissions.ReflectionPermissionAttribute.RestrictedMemberAccess%2A>ve bu nedenle, kısmi güven altında çalışmaz. İş akışı <xref:System.Activities.Expressions.LambdaValue%601> söz konusu ifadelerden türetilen etkinliklerle değiştirmelisiniz <xref:System.Activities.CodeActivity%601>. biçimindeki telefon numarasıdır.

7. İfadeleri kullanarak derlenemez <xref:System.Activities.XamlIntegration.TextExpressionCompiler> veya Visual Basic derleyici kısmi güvende barındırılan, ancak daha önce derlenmiş ifadeleri çalıştırılabilir.

8. Kullanan tek bir derleme [Düzey 2 saydamlık](https://aka.ms/Level2Transparency) kullanılamaz [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] tam güven ve [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] kısmi güven.

## <a name="BKMK_NewDesignerCapabilites"></a> Yeni Tasarımcı özellikleri

### <a name="BKMK_DesignerSearch"></a> Tasarımcı arama

Daha büyük iş akışlarını daha kolay yönetilebilir hale getirmek için iş akışları artık anahtar sözcüğü ile aranabilir. Bu özellik, yalnızca Visual Studio içinde kullanılabilir; Bu özellik, yeniden barındırılan tasarımcıda kullanılamıyor. Aramalar iki tür vardır:

- İle başlatılan Hızlı Bul **Ctrl + F** veya **Düzenle**, **Bul ve Değiştir**, **Hızlı Bul**.

- İle başlatılan dosyalarına Bul **Ctrl + SHIFT + F** veya **Düzenle**, **Bul ve Değiştir**, **dosyalarda Bul**.

Replace desteklenmediğini unutmayın.

#### <a name="BKMK_QuickFind"></a> Hızlı Bul

İş akışlarında arama anahtar sözcükleri aşağıdaki Tasarımcı öğeleri eşleşir:

- Özelliklerini <xref:System.Activities.Activity> nesneleri <xref:System.Activities.Statements.FlowNode> nesneleri <xref:System.Activities.Statements.State> nesneleri <xref:System.Activities.Statements.Transition> nesneleri ve diğer özel akış denetimi öğeleri.

- Değişkenler

- Arguments

- İfadeler

Hızlı Bul tasarımcının üzerinde gerçekleştirilen <xref:System.Activities.Presentation.Model.ModelItem> ağaç. İş akışı tanımı içeri aktarılan ad alanlarını Hızlı Bul'u bulamaz.

#### <a name="BKMK_FindInFiles"></a> Dosyalarda Bul

İş akışı dosyalarını gerçek içeriği akışlarında arama anahtar sözcükleri eşleşir. Visual Studio Bul sonuçları görünümü bölmesinde arama sonuçları gösterilir. İş Akışı Tasarımcısı'nda eşleşme içeren etkinliğine sonucu öğesinin çift gider.

### <a name="BKMK_VariableDeleteContextMenu"></a> Değişken ve bağımsız değişken Tasarımcısı'nda bağlam menüsü öğesi silme

İçinde [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], değişkenler ve bağımsız değişkenleri yalnızca silinmesi klavyeyi kullanarak Tasarımcısı'nda. İle başlayarak [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], değişkenler ve bağımsız değişkenler bağlam menüsü kullanılarak silinebilir.

Aşağıdaki ekran görüntüsünde, değişken ve bağımsız değişken Tasarımcı bağlam menüsünü gösterir.

![Değişken ve bağımsız değişken Tasarımcı bağlam menüsü](./media/designercontextmenu.png "DesignerContextMenu")

### <a name="BKMK_AutoSurround"></a> Otomatik-çevrelemeyi dizisi

Bir iş akışı veya belirli bir kapsayıcı etkinlikleri (gibi <xref:System.Activities.Statements.NoPersistScope>) yalnızca tek bir gövde etkinlik içerebilir, ikinci etkinlik ekleme, geliştirici ilk etkinliği silin, eklemek gerekli bir <xref:System.Activities.Statements.Sequence> etkinlik ve ardından her iki etkinlik için ekleme sıralı etkinlik. İle başlayarak [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], ikinci bir etkinlik Tasarımcı yüzeyine eklerken bir `Sequence` etkinlik otomatik olarak oluşturulacak hem etkinlikleri sarmalamak için.

Aşağıdaki ekran görüntüsü gösterildiği bir `WriteLine` etkinliğinde `Body` , bir `NoPersistScope`.

![Otomatik&#45;çevreleyen bırakma konumu](./media/autosurround1.png "AutoSurround1")

Aşağıdaki ekran görüntüsünde otomatik olarak oluşturulan gösterilmektedir `Sequence` etkinliğinde `Body` ikinci zaman `WriteLine` ilk düştü.

![Sıralı etkinlik otomatik olarak oluşturulan](./media/autosurround2.png "AutoSurround2")

### <a name="BKMK_PanMode"></a> PAN modu

Büyük bir iş akışı Tasarımcısı'nda daha kolay gezinme için kaydırma modu, kaydırma çubuklarını gerek kalmadan yerine geliştiricinin iş akışının görünür bölümünün taşımak için tıklayın ve sürükleyin izin vererek etkinleştirilebilir. PAN modunu etkinleştirmek için tasarımcının sağ alt köşesindeki düğmesidir.

Aşağıdaki ekran görüntüsünde, iş akışı Tasarımcısı alt sağ köşesinde bulunan pan düğmesini gösterir.

![İş Akışı Tasarımcısı'nda PAN düğmesi](./media/panbutton.png "PanButton")

Orta fare düğmesine veya Ara çubuğuna iş akışı Tasarımcısı kaydırmak için de kullanılabilir.

### <a name="BKMK_MultiSelect"></a> Çoklu seçim

Birden çok etkinlik, bunları (kaydırma modu etkin değilken) çevresinde bir dikdörtgen sürükleyerek veya Ctrl tuşunu basılı tutarak bir seferde seçilebilir ve istenen etkinlikleri tek tek tıklayın.

Birden çok etkinlik seçimleri ayrıca sürüklediğiniz ve tasarımcı içinde bırakılan ve bağlam menüsünü kullanarak da bulunulması.

### <a name="BKMK_DocumentOutline"></a> İş akışı öğelerinin anahat görünümü

Hiyerarşik iş akışları gidin daha kolay hale getirmek için bir iş akışı bileşenleri, ağaç stili ana görünümünde gösterilir. Anahat görünümünde görüntülenen **belge anahattı** görünümü. Bu görünüm, üstteki menüden açmak için seçmeniz **görünümü**, **diğer Windows**, **belge anahattı**, ya da Ctrl W, u tuşuna basın Ana görünümünde bir düğüm tıklayarak ilgili etkinlik iş akışı tasarımcısında gider ve anahat görünümü Tasarımcısı'nda seçili etkinlikler göstermek için güncelleştirilir.

Aşağıdaki ekran görüntüsünde tamamlanan iş akışından [başlangıç Öğreticisi](getting-started-tutorial.md) sıralı bir iş akışı ile ana hat görünümü gösterilir.

![Anahat iş akışı Tasarımcısı'nda görünümü](./media/outlineviewinworkflowdesigner.jpg "OutlineViewinWorkflowDesigner")

### <a name="BKMK_CSharpExpressions"></a> C# ifadeleri

Öncesinde [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], tüm ifadeleri iş akışlarında yalnızca Visual Basic'te yazılmış. İçinde [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], Visual Basic deyimleri yalnızca Visual Basic kullanılarak oluşturulan projeler için kullanılır. Visual C# projeleri artık C# ifadeleri için kullanın. Tam olarak işlevsel bir C# ifade Düzenleyicisi dilbilgisi vurgulama ve IntelliSense gibi hangi özellikler sağlanır. C# iş akışı projeleri Visual Basic deyimleri kullanacak önceki sürümlerinde oluşturulan çalışmaya devam eder.

C# ifadeleri tasarım zamanında doğrulanır. C# ifadelerini hatalar bir kırmızı dalgalı çizgi işaretlenir.

C# ifadeleri hakkında daha fazla bilgi için bkz: [C# ifadelerini](csharp-expressions.md).

### <a name="BKMK_Visibility"></a> Daha fazla denetim görünürlüğünü Kabuk çubuğu ve üstbilgi öğeleri

Yeniden barındırılan tasarımcıda, bazı standart kullanıcı Arabirimi denetimleri için belirli bir iş akışı anlamı olmayabilir ve kapalı olabilir. İçinde [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], bu özelleştirme yalnızca Tasarımcısı'nın altındaki Kabuk çubuğu tarafından desteklenir. İçinde [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], kabuk üstbilgi öğeleri Tasarımcı üst kısmındaki görünürlüğünü ayarlayarak ayarlanabilir <xref:System.Activities.Presentation.View.DesignerView.WorkflowShellHeaderItemsVisibility%2A> uygun <xref:System.Activities.Presentation.View.ShellHeaderItemsVisibility> değeri.

### <a name="BKMK_AutoConnect"></a> Otomatik bağlanma ve akış ve Durum makinesi iş akışlarında otomatik Ekle

İçinde [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], bir akış çizelgesi iş akışı düğümleri arasındaki bağlantıları el ile eklenen gerekiyordu. İçinde [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], akış ve Durum makinesi düğüme sahip bir etkinlik araç kutusunu tasarımcı yüzeyine sürüklediğinizde görünür hale gelmiş noktalarını otomatik olarak bağlan. Bir etkinlik otomatik olarak bu noktalarından birine bırakarak, gerekli bağlantı birlikte etkinlik ekler.

Aşağıdaki ekran görüntüsünde bir etkinlik araç kutusundan sürüklendiğinde görünür hale gelmiş eki noktalarını gösterir.

![Otomatik bağlanma noktalarını gösteren akış çizelgesi başlangıç düğümü](./media/autoconnect1.png "Autoconnect1")

Etkinlikler de akış düğüm ve düğüm iki düğüm arasındaki otomatik olarak eklemek üzere durumları arasında bağlantılar sürüklenebilen. Aşağıdaki ekran görüntüsünde vurgulanan bağlantı satırı burada etkinlikler araç kutusundan sürüklediğiniz ve olması bırakılan gösterir.

![Otomatik&#45;etkinlikleri silmek için tanıtıcı eklemek](./media/autoinsert.png "Autoinsert")

### <a name="BKMK_Annotations"></a> Tasarımcı ek açıklamaları

Daha büyük iş akışları geliştirme kolaylaştırmak için tasarımcı tasarım süreci izlemenize yardımcı olması için ekleme ek açıklamalarını destekler. Ek açıklama, etkinlikleri, durumları, akış düğümleri, değişkenler ve bağımsız değişkenler eklenebilir. Aşağıdaki ekran görüntüsünde, ek açıklamalar tasarımcıya eklemek için kullanılan bağlam menüsünü gösterir.

![Ek açıklama bağlam menüsü](./media/annotationdialog.png "annotationdialog")

### <a name="debugging-states"></a>Hata ayıklama durumları

İçinde [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], etkinlik olmayan öğeler desteklemediği hata ayıklama kesme noktalarına olduğundan yürütme birimleri değildi. Bu sürüm için kesme noktaları eklemek için bir mekanizma sağlar <xref:System.Activities.Statements.State> nesneleri. Üzerinde bir kesme noktası ayarlandığında bir <xref:System.Activities.Statements.State>yürütme durumu geçirildiğinde bozar, önce girdisini etkinlikler veya tetikleyicileri zamanlanır.

### <a name="BKMK_ActivityDelegates"></a> Tanımlama ve tasarımcıda ActivityDelegate nesneleri kullanma

Etkinlikler [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] kullanılan <xref:System.Activities.ActivityDelegate> burada diğer bölümlerini bir iş akışı ile bir iş akışının yürütme destekliyordu, ancak bu yürütme noktaları genellikle kullanarak gerekli ciddi miktarda bir kod yürütme noktaları ortaya çıkarmak için nesne. Bu sürümde, geliştiricilerin tanımlayabilir ve iş akışı Tasarımcısı kullanarak etkinlik temsilcileri kullanma. Daha fazla bilgi için [nasıl yapılır: Tanımlama ve iş akışı tasarımcısında etkinlik temsilcileri kullanma](/visualstudio/workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer).

### <a name="BKMK_BuildTimeValidation"></a> Derleme zamanı doğrulama

İçinde [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], iş akışı doğrulama hataları iş akışı projesi derleme sırasında derleme hataları sayılan olmayan. Bu, bir iş akışı oluşturma geliyordu bile iş akışı doğrulama hatalarını zamanki proje başarılı. İçinde [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], iş akışı doğrulama hatalarına neden başarısız için yapı.

### <a name="BKMK_DesignTimeValidation"></a> Tasarım zamanı arka plan doğrulama

İçinde [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], iş akışları kullanıcı Arabirimi karmaşık ya da zaman harcayan doğrulama işlemleri sırasında potansiyel olarak askıda kalabilir ön plan işlemi olarak doğrulandı. Böylece kullanıcı Arabirimi engellenmez artık iş akışı doğrulamasındaki bir arka plan iş parçacığı üzerinde gerçekleşir.

### <a name="BKMK_ViewState"></a> XAML dosyaları ayrı bir konumda bulunan görünüm durumu

İçinde [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], bir iş akışı için Görünüm durumu bilgilerini arasında birçok farklı konumlara XAML dosyasında depolanır. Bu, doğrudan XAML okuma veya Görünüm durumu bilgilerini kaldırmak için kod yazma isteyen geliştiriciler için kullanışsız olur. İçinde [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], ilişkin görünüm durumu bilgilerinin XAML dosyasında XAML dosyası içinde ayrı bir öğe olarak serileştirilir. Kolayca geliştiriciler bulun ve etkinliğin görünüm durumu bilgilerini düzenlemek veya Görünüm durumu tamamen kaldırabilirsiniz.

### <a name="BKMK_ExpressionExtensibility"></a> İfade genişletilebilirliği

İçinde [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], kendi ifade ve ifade yazma iş akışı Tasarımcısı ile takılı deneyimi oluşturmak üzere geliştiricilere bir yol sunuyoruz.

### <a name="BKMK_BackwardCompatRehostedDesigner"></a> İş akışı 4.5 özellikleri yeniden barındırılan tasarımcıda katılımı

Geriye dönük uyumluluğu korumak için bazı yeni özellikler dahil [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] yeniden barındırılan tasarımcıda varsayılan olarak etkin değildir. Bu yeniden barındırılan Tasarımcısı'nı kullanan mevcut uygulamaları en son sürüme güncelleştirerek etkilenmemesini sağlamak içindir. Yeniden barındırılan tasarımcıda yeni özellikleri etkinleştirmek için ya da ayarlayın <xref:System.Activities.Presentation.DesignerConfigurationService.TargetFrameworkName%2A> ".NET Framework 4.5" ya da kümesi tek tek üyeleri <xref:System.Activities.Presentation.DesignerConfigurationService> tek tek özellikleri etkinleştirmek için.

## <a name="BKMK_NewWFModels"></a> Yeni iş akışı geliştirme modelleri

Bu sürüm, akış ve sıralı iş akışı geliştirme modelleri ek olarak, durum makine iş akışları ve sözleşme öncelikli iş akışı hizmetleri içerir.

### <a name="BKMK_StateMachine"></a> Durum makinesi iş akışları

Durum makinesi iş akışları, .NET Framework 4, sürüm 4.0.1'in parçası olarak sunulmuştur [Microsoft .NET Framework 4 Platform Update 1](https://go.microsoft.com/fwlink/?LinkID=215092). Bu, birkaç yeni sınıfı ve geliştiricilerin durum makine iş akışları oluşturmak izin verilen etkinlikleri güncelleştirmenin. Bu sınıflar ve etkinlikler için güncelleştirilen [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]. Güncelleştirmeler şunları içerir:

1. Durumlar üzerinde kesme noktaları ayarlama olanağı

2. İş akışı tasarımcısında geçişleri yapıştırın olanağı

3. Paylaşılan tetikleyici geçişi oluşumu için tasarımcı desteği

4. Etkinlikler dahil olmak üzere durum makine iş akışları oluşturmak için kullanılan: <xref:System.Activities.Statements.StateMachine>, <xref:System.Activities.Statements.State>, ve <xref:System.Activities.Statements.Transition>

Aşağıdaki ekran görüntüsünde tamamlanan durum makine iş akışından gösterilmektedir [başlangıç Öğreticisi](getting-started-tutorial.md) adım [nasıl yapılır: Bir Durum makinesi iş akışı oluşturmak](how-to-create-a-state-machine-workflow.md).

![Durum makinesi iş akışı tamamlandı](./media/wfstatemachinegettingstartedtutorialcomplete.JPG "WFStateMachineGettingStartedTutorialComplete")

Durum makine iş akışları oluşturma hakkında daha fazla bilgi için bkz. [durum makine iş akışları](state-machine-workflows.md).

### <a name="BKMK_ContractFirst"></a> Sözleşme öncelikli iş akışı geliştirme

Bir kod sözleşmesi ilk tasarlayın ve ardından Visual Studio'da birkaç tıklama ile her bir işlemi temsil eden araç kutusunda otomatik olarak bir etkinlik şablonu oluşturmak Geliştirici sözleşme öncelikli iş akışı geliştirme aracı sağlar. Bu etkinlikler, ardından anlaşmada tanımlanan işlemleri uygulayan bir iş akışı oluşturmak için kullanılır. İş Akışı Tasarımcısı bu işlemleri uygulanır ve iş akışı imzası sözleşme imzayla eşleşen emin olmak için iş akışı hizmeti doğrular. Geliştirici, ayrıca bir iş akışı hizmeti uygulanan sözleşmelerin koleksiyonu ile ilişkilendirebilirsiniz. Sözleşme öncelikli iş akışı hizmet geliştirme hakkında daha fazla bilgi için bkz. [nasıl yapılır: Mevcut bir hizmet anlaşmasını kullanan iş akışı hizmeti oluşturma](how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md).
