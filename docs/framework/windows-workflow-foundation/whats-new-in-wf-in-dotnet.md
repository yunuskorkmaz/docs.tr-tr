---
title: .NET 4.5 içinde Windows Workflow Foundation’daki Yenilikler
ms.date: 03/30/2017
ms.assetid: 195c43a8-e0a8-43d9-aead-d65a9e6751ec
ms.openlocfilehash: 80919dd7a726cbac5fa13680e0c79292745a7bca
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837590"
---
# <a name="whats-new-in-windows-workflow-foundation-in-net-45"></a>.NET 4.5 içinde Windows Workflow Foundation’daki Yenilikler

.NET Framework 4,5 ' de Windows Workflow Foundation (WF), yeni etkinlikler, tasarımcı özellikleri ve iş akışı geliştirme modelleri gibi birçok yeni özellik sunmaktadır. .NET Framework 4,5 ' de tanıtılan yeni iş akışı özelliklerinin birçoğu, yeniden barındırılan iş akışı tasarımcısında desteklenir. Desteklenen yeni özellikler hakkında daha fazla bilgi için bkz. [yeniden barındırılan iş akışı Tasarımcısı yeni Workflow Foundation 4,5 özellikleri Için destek](wf-features-in-the-rehosted-workflow-designer.md). .NET 3,0 ve .NET 3,5 iş akışı uygulamalarını en son sürümü kullanacak şekilde geçirme hakkında daha fazla bilgi için bkz. [Geçiş Kılavuzu](migration-guidance.md). Bu konu, .NET Framework 4,5 ' de tanıtılan yeni iş akışı özelliklerine genel bir bakış sağlar.

> [!WARNING]
> .NET Framework 4,5 ' de tanıtılan yeni Windows Workflow Foundation özellikleri, Framework 'ün önceki sürümlerini hedefleyen projeler için kullanılamaz. .NET Framework 4,5 ' i hedefleyen bir proje Framework 'ün önceki bir sürümüne yeniden hedeflerse, bazı sorunlar meydana gelebilir.
>
> - C#ifadeler, **xaml 'de Ileti değeri ayarlanmış**şekilde tasarımcıda yer alır.
> - Aşağıdaki hata da dahil olmak üzere pek çok derleme hatası meydana gelir.
>
> **Dosya biçimi geçerli hedefleme çerçevesiyle uyumlu değil. Dosya biçimini dönüştürmek için lütfen dosyayı açık olarak kaydedin. Bu hata iletisi, dosyayı kaydettikten ve tasarımcıyı yeniden açıldıktan sonra kalır.**

## <a name="BKMK_Versioning"></a>İş akışı sürümü oluşturma

.NET Framework 4,5 yeni <xref:System.Activities.WorkflowIdentity> sınıfını temel alarak birkaç yeni sürüm oluşturma özelliği sunmuştur. <xref:System.Activities.WorkflowIdentity>, iş akışı uygulaması yazarlarına, kalıcı bir iş akışı örneğini tanımıyla eşlemek için bir mekanizma sağlar.

- <xref:System.Activities.WorkflowApplication> barındırmanın kullanıldığı geliştiriciler, bir iş akışının birden çok sürümünü yan yana barındırmayı etkinleştirmek için <xref:System.Activities.WorkflowIdentity> kullanabilir. Kalıcı iş akışı örnekleri yeni <xref:System.Activities.WorkflowApplicationInstance> sınıfı kullanılarak yüklenebilir ve ardından <xref:System.Activities.WorkflowApplicationInstance.DefinitionIdentity%2A> ana bilgisayar tarafından <xref:System.Activities.WorkflowApplication>örneği oluşturulurken doğru iş akışı tanımının doğru sürümünü sağlamak üzere kullanılabilir. Daha fazla bilgi için bkz. [Workflowwıdentity ve sürüm oluşturma](using-workflowidentity-and-versioning.md) ve [nasıl yapılır: bir Iş akışının birden çok sürümünü yan yana barındırma](how-to-host-multiple-versions-of-a-workflow-side-by-side.md).

- <xref:System.ServiceModel.WorkflowServiceHost> artık çok sürümlü bir ana bilgisayar. Bir iş akışı hizmeti 'nin yeni bir sürümü dağıtıldığında, yeni hizmet kullanılarak yeni örnekler oluşturulur, ancak mevcut örnekler önceki sürümü kullanılarak tamamlanır. Daha fazla bilgi için bkz. [WorkflowServiceHost 'Da yan yana sürüm oluşturma](../wcf/feature-details/side-by-side-versioning-in-workflowservicehost.md).

- Kalıcı bir iş akışı örneğinin tanımını güncelleştirmeye yönelik bir mekanizma sağlayan dinamik güncelleştirme tanıtılmıştır. Daha fazla bilgi için bkz. [dinamik güncelleştirme](dynamic-update.md) ve [nasıl yapılır: çalışan bir Iş akışı örneğinin tanımını güncelleştirme](how-to-update-the-definition-of-a-running-workflow-instance.md).

- .NET Framework 4 veritabanı betikleri kullanılarak oluşturulan kalıcı veritabanlarını yükseltmek için bir SqlWorkflowInstanceStoreSchemaUpgrade. SQL veritabanı betiği sağlanır. Bu betik, .NET Framework 4,5 ' de tanıtılan yeni sürüm oluşturma özelliklerini desteklemek için 4 kalıcılık veritabanını .NET Framework güncelleştirir. Veritabanındaki kalıcı iş akışı örneklerine varsayılan sürüm oluşturma değerleri verilir ve yan yana yürütmeye ve Dinamik güncelleştirmeye katılabilirler. Daha fazla bilgi için bkz. [Iş akışı sürümü oluşturmayı desteklemek için .NET Framework 4 kalıcılık veritabanlarını yükseltme](using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases).

## <a name="BKMK_NewActivities"></a>İşlemleri

Yerleşik etkinlik kitaplığı, yeni etkinlikler ve mevcut etkinliklere yönelik yeni özellikler içerir.

### <a name="BKMK_NoPersistScope"></a>NoPersist kapsamı

<xref:System.Activities.Statements.NoPersistScope>, NoPersistScope 'un alt etkinlikleri yürütülerek bir iş akışının kalıcı olmasını önleyen yeni bir kapsayıcı etkinliğidir. Bu, iş akışının, dosya tutamaçları gibi makineye özel kaynakları kullanırken veya veritabanı işlemleri sırasında olduğu gibi, iş akışının kalıcı olması için uygun olmadığı senaryolarda faydalıdır. Daha önce, bir etkinliğin yürütülmesi sırasında kalıcılığın oluşmasını önlemek için, <xref:System.Activities.NoPersistHandle> kullanan özel bir <xref:System.Activities.NativeActivity> gerekiyordu.

### <a name="BKMK_NewFlowchartCapabilities"></a>Yeni akış çizelgesi özellikleri

Akış çizelgeleri .NET Framework 4,5 için güncelleştirilir ve aşağıdaki yeni yeteneklere sahiptir:

- Bir <xref:System.Activities.Statements.FlowSwitch%601> veya <xref:System.Activities.Statements.FlowDecision> etkinliğinin `DisplayName` özelliği düzenlenebilir. Bu, etkinlik Tasarımcısı 'nın etkinliğin amacı hakkında daha fazla bilgi göstermesini sağlar.

- Akış çizelgeleriyle <xref:System.Activities.Statements.Flowchart.ValidateUnconnectedNodes%2A>adlı yeni bir özellik vardır. Bu özellik için varsayılan değer `False`. Bu özellik `True`olarak ayarlandıysa, bağlı olmayan akış çizelgesi düğümleri doğrulama hataları oluşturur.

## <a name="support-for-partial-trust"></a>Kısmi güven desteği

.NET Framework 4 ' teki iş akışları tam olarak güvenilen bir uygulama etki alanı gerektirir. .NET Framework 4,5 ' de, iş akışları kısmi güven ortamında çalışabilir. Kısmi güven ortamında, üçüncü taraf bileşenleri, ana bilgisayarın kaynaklarına tam erişim verilmeden kullanılabilir. Kısmi güvende iş akışlarını çalıştırmaya ilişkin bazı sorunlar şunlardır:

1. <xref:System.Activities.Statements.Interop> etkinliğinde bulunan eski bileşenleri (kurallar dahil) kullanmak kısmi güven altında desteklenmez.

2. <xref:System.ServiceModel.WorkflowServiceHost> ' de kısmi güvende iş akışlarının çalıştırılması desteklenmez.

3. Kısmi güven senaryosunda kalıcı özel durumlar olası bir güvenlik tehditlidir. Özel durumların kalıcı olmasını devre dışı bırakmak için, <xref:System.Activities.ExceptionPersistenceExtension> türünde bir uzantı projeye, kalıcı özel durumların geri çevirmek için eklenmelidir. Aşağıdaki kod örneği, bu türün nasıl uygulanacağını gösterir.

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

     Özel durumların serileştirilmemesini sağlamak için, özel durumların bir <xref:System.Activities.Statements.NoPersistScope>içinde kullanıldığından emin olun.

4. Etkinlik yazarları, iş akışı çalışma zamanının otomatik olarak türe karşı yansıma yürütmesini önlemek için <xref:System.Activities.Activity.CacheMetadata%2A> geçersiz kılmalıdır. Bağımsız değişkenler ve alt etkinlikler null olmamalı ve <xref:System.Activities.ActivityMetadata.Bind%2A> açık olarak çağrılmalıdır. <xref:System.Activities.Activity.CacheMetadata%2A>geçersiz kılma hakkında daha fazla bilgi için bkz. [verileri CacheMetadata Ile gösterme](exposing-data-with-cachemetadata.md). Ayrıca, yansıma tarafından oluşturulmasını önlemek için, `internal` veya **Private** olan bir türdeki bağımsız değişkenlerin örnekleri <xref:System.Activities.Activity.CacheMetadata%2A> açıkça oluşturulmalıdır.

5. Türler, serileştirme için <xref:System.Runtime.Serialization.ISerializable> veya <xref:System.SerializableAttribute> kullanmaz; seri hale getirilecek türler <xref:System.Runtime.Serialization.DataContractSerializer>desteklemelidir.

6. <xref:System.Activities.Expressions.LambdaValue%601> kullanan ifadeler <xref:System.Security.Permissions.ReflectionPermissionAttribute.RestrictedMemberAccess%2A>gerektirir ve bu nedenle kısmi güven altında çalışmayacaktır. <xref:System.Activities.Expressions.LambdaValue%601> kullanan iş akışları, bu ifadelerin <xref:System.Activities.CodeActivity%601>türetilen etkinliklerle değiştirilmesini sağlamalıdır. .

7. İfadeler <xref:System.Activities.XamlIntegration.TextExpressionCompiler> veya kısmi güvende Visual Basic barındırılan derleyici kullanılarak derlenemez, ancak önceden derlenen ifadeler çalıştırılabilir.

8. [Düzey 2 saydamlığı](https://aka.ms/Level2Transparency) kullanan tek bir derleme .NET Framework 4 ' te, tam güvende [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] ve kısmi güvende [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] kullanılamaz.

## <a name="BKMK_NewDesignerCapabilites"></a>Yeni tasarımcı özellikleri

### <a name="BKMK_DesignerSearch"></a>Tasarımcı arama

Daha büyük iş akışlarını daha yönetilebilir hale getirmek için iş akışları artık anahtar sözcüğü ile aranabilecek. Bu özellik yalnızca Visual Studio 'da kullanılabilir; Bu özellik yeniden barındırılan bir tasarımcıda kullanılamaz. Kullanılabilecek iki tür arama vardır:

- Hızlı bul, **CTRL + F** ya da **Düzenle**, **Bul ve Değiştir**, **hızlı bul**ile başlatıldı.

- Dosyalarda bul, **CTRL + SHIFT + F** ile başlatılan veya **Düzenle**, **Bul ve Değiştir**, **dosyalarda bul**.

Değiştirme 'nin desteklenmediğini unutmayın.

#### <a name="BKMK_QuickFind"></a>Hızlı bul

İş akışlarında aranan anahtar sözcükler aşağıdaki tasarımcı öğeleriyle eşleşir:

- <xref:System.Activities.Activity> nesnelerinin özellikleri, <xref:System.Activities.Statements.FlowNode> nesneleri, <xref:System.Activities.Statements.State> nesneleri, <xref:System.Activities.Statements.Transition> nesneleri ve diğer özel akış denetimi öğeleri.

- Değişkenler

- Arguments

- {1&gt;İfadeler&lt;1}

Hızlı bul, tasarımcının <xref:System.Activities.Presentation.Model.ModelItem> ağacında gerçekleştirilir. Hızlı bul, iş akışı tanımına içeri aktarılan ad alanlarını bulamaz.

#### <a name="BKMK_FindInFiles"></a>Dosyalarda bul

İş akışlarında aranan anahtar sözcükler, iş akışı dosyalarının gerçek içeriğiyle eşleşmeyecektir. Arama sonuçları, Visual Studio bul Sonuçlar görünümü bölmesinde gösterilir. Sonuç öğesine çift tıklamak, iş akışı tasarımcısında eşleşmeyi içeren etkinliğe gidecektir.

### <a name="BKMK_VariableDeleteContextMenu"></a>Değişken ve bağımsız değişken tasarımcısında bağlam menüsü öğesini Sil

.NET Framework 4 ' te, değişkenler ve bağımsız değişkenler yalnızca klavye kullanılarak tasarımcıda silinebilir. .NET Framework 4,5 ' den başlayarak, değişkenler ve bağımsız değişkenler bağlam menüsü kullanılarak silinebilir.

Aşağıdaki ekran görüntüsünde, değişken ve bağımsız değişken tasarımcı bağlam menüsü gösterilmektedir.

![Değişken ve bağımsız değişken Tasarımcısı bağlam menüsü](./media/whats-new-in-wf-in-dotnet/designer-context-menu.png)

### <a name="BKMK_AutoSurround"></a>Sırayla Otomatik sarma

Bir iş akışı veya bazı kapsayıcı Etkinlikleri (örneğin, <xref:System.Activities.Statements.NoPersistScope>) yalnızca tek bir gövde etkinliği içerebildiği için, ikinci bir etkinlik eklemek geliştiricinin ilk etkinliği silmesi, bir <xref:System.Activities.Statements.Sequence> etkinliği eklemesi ve ardından her iki etkinliği de sıralı etkinliğe eklemesi gerekir. .NET Framework 4,5 ' den başlayarak, tasarımcı yüzeyine ikinci bir etkinlik eklenirken, her iki etkinliği de kaydırmak için `Sequence` bir etkinlik otomatik olarak oluşturulur.

Aşağıdaki ekran görüntüsünde bir `NoPersistScope``Body` `WriteLine` etkinlik gösterilmektedir.

![NoPersistScope etkinliğinin gövdesinde bir WriteLine etkinliği.](./media/whats-new-in-wf-in-dotnet/auto-surround-write-line-activity.png)

Aşağıdaki ekran görüntüsünde ikinci bir `WriteLine` ilk altına bırakıldığında `Body` otomatik olarak oluşturulan `Sequence` etkinliği gösterilmektedir.

![NoPersistScope gövdesinde otomatik olarak oluşturulan bir sıra.](./media/whats-new-in-wf-in-dotnet/auto-surround-sequence-activity.png)

### <a name="BKMK_PanMode"></a>Kaydırma modu

Tasarımcıda büyük bir iş akışında daha kolay gezinmek için, kaydırma modu etkinleştirilebilir, böylece Geliştirici, kaydırma çubuklarının kullanılmasına gerek kalmadan iş akışının görünür kısmını taşımak için tıklamasına ve sürüklemesine olanak tanır. Yatay kaydırma modunu etkinleştirmek için düğme, tasarımcının sağ alt köşesindedir.

Aşağıdaki ekran görüntüsünde, iş akışı tasarımcısının sağ alt köşesinde bulunan kaydır düğmesi gösterilmektedir.

![İş akışı tasarımcısında kaydırma düğmesi vurgulandı.](./media/whats-new-in-wf-in-dotnet/pan-button-workflow-designer.png)

Orta fare düğmesi veya boşluk çubuğu, iş akışı tasarımcısını kaydırmak için de kullanılabilir.

### <a name="BKMK_MultiSelect"></a>Çoklu seçim

Birden çok etkinlik tek seferde seçilebilir (kaydırma modu etkin değil), ya da CTRL tuşunu basılı tutarak istenen etkinliklere tek tek tıklayın.

Birden çok etkinlik seçimi de tasarımcı içinde sürüklenip bırakılabilir ve bağlam menüsü kullanılarak da etkileşim edilebilir.

### <a name="BKMK_DocumentOutline"></a>İş akışı öğelerinin Ana Hat görünümü

Hiyerarşik iş akışlarının gezinmesinin daha kolay olmasını sağlamak için bir iş akışının bileşenleri ağaç stili bir anahat görünümünde gösterilir. Ana hat görünümü **Belge anahat** görünümünde görüntülenir. Bu görünümü açmak için, üstteki menüden **Görünüm**, **diğer pencereler**, **Belge Anahattı**' nı seçin veya CTRL W, U tuşlarına basın. Ana hat görünümündeki bir düğüme tıkladığınızda, iş akışı tasarımcısında ilgili etkinliğe gidebilirsiniz ve ana hat görünümü tasarımcıda seçilen etkinlikleri gösterecek şekilde güncelleştirilir.

Başlangıç [öğreticisindeki](getting-started-tutorial.md) tamamlanan iş akışının aşağıdaki ekran görüntüsü, sıralı bir iş akışı ile ana hat görünümünü gösterir.

![Visual Studio 'da sıralı bir iş akışı ile ana hat görünümünün ekran görüntüsü.](./media/whats-new-in-wf-in-dotnet/outline-view-in-workflow-designer.jpg)

### <a name="BKMK_CSharpExpressions"></a>C# İfadeler

.NET Framework 4,5 ' dan önce, iş akışlarındaki tüm ifadeler yalnızca Visual Basic yazdırılabilir. .NET Framework 4,5 ' de Visual Basic ifadeler yalnızca Visual Basic kullanılarak oluşturulan projeler için kullanılır. Artık C# Visual projeleri ifadeler C# için kullanılır. Tam işlevli C# bir ifade düzenleyicisine, dilbilgisi vurgulama ve IntelliSense gibi yetenekler sağlanır. C#önceki sürümlerde oluşturulan Visual Basic ifadeleri kullanan iş akışı projeleri çalışmaya devam edecektir.

C#ifadeler tasarım zamanında onaylanır. İfadelerdeki C# hatalar, kırmızı dalgalı alt çizgiyle işaretlenir.

İfadeler hakkında C# daha fazla bilgi için bkz [ C# . ifadeler](csharp-expressions.md).

### <a name="BKMK_Visibility"></a>Kabuk çubuğu ve üst bilgi öğelerinin görünürlüğü hakkında daha fazla denetim

Yeniden barındırılan bir tasarımcıda, bazı standart Kullanıcı arabirimi denetimlerinin belirli bir iş akışı için anlamı olmayabilir ve kapatılabilir. .NET Framework 4 ' te bu özelleştirme yalnızca tasarımcının alt kısmındaki kabuk çubuğu tarafından desteklenir. .NET Framework 4,5 ' de, tasarımcı 'nın en üstündeki kabuk üst bilgi öğelerinin görünürlüğü, uygun <xref:System.Activities.Presentation.View.ShellHeaderItemsVisibility> değeri ile <xref:System.Activities.Presentation.View.DesignerView.WorkflowShellHeaderItemsVisibility%2A> ayarlanarak ayarlanabilir.

### <a name="BKMK_AutoConnect"></a>Akış Çizelgesine ve durum makinesi iş akışlarına otomatik bağlan ve otomatik ekle

.NET Framework 4 ' te, bir akış çizelgesi iş akışında düğümler arasındaki bağlantıların el ile eklenmesi gerekiyordu. .NET Framework 4,5 ' de, akış çizelgesi ve durum makinesi düğümlerinde, bir etkinlik araç kutusundan tasarımcı yüzeyine sürüklendiğinde görünür hale gelen otomatik bağlantı noktaları bulunur. Bu noktaların birine bir etkinliğin atılması, etkinliği gereken bağlantıyla birlikte otomatik olarak ekler.

Aşağıdaki ekran görüntüsünde, bir etkinlik araç kutusundan sürüklendiğinde görünür hale gelen ek noktaları gösterilmektedir.

![Akış çizelgesi başlangıç düğümü otomatik bağlantı noktalarını gösterir](./media/whats-new-in-wf-in-dotnet/auto-connect-points-start-node.png)

Ayrıca, iki düğüm arasında düğümü otomatik olarak eklemek için, aynı zamanda akış çizelgesi düğümleri ve durumlar arasındaki bağlantılar üzerinde de değiştirilebilir. Aşağıdaki ekran görüntüsünde, etkinliklerin araç kutusundan sürüklenip bırakılbileceği vurgulanan bağlantı çizgisi gösterilmektedir.

![Bırakma etkinlikleri için otomatik ekleme tutamacı](./media/whats-new-in-wf-in-dotnet/auto-insert-connecting-line.png)

### <a name="BKMK_Annotations"></a>Tasarımcı ek açıklamaları

Daha büyük iş akışlarının geliştirilmesini kolaylaştırmak için, tasarımcı artık tasarım sürecini izlemeye yardımcı olan ek açıklamalar eklemeyi desteklemektedir. Ek açıklama, etkinliklere, durumlara, akış çizelgesi düğümlerine, değişkenlere ve bağımsız değişkenlere eklenebilir. Aşağıdaki ekran görüntüsünde, tasarımcıya ek açıklamalar eklemek için kullanılan bağlam menüsü gösterilmektedir.

![Ek açıklama ekleme menüsünü gösteren ekran görüntüsü.](./media/whats-new-in-wf-in-dotnet/designer-annotations-context-menu.png)

### <a name="debugging-states"></a>Hata ayıklama durumları

.NET Framework 4 ' te, etkinlik dışı öğeler yürütme birimleri olmadığından hata ayıklama kesme noktalarını desteklemez. Bu sürüm <xref:System.Activities.Statements.State> nesnelerine kesme noktaları eklemek için bir mekanizma sağlar. Bir <xref:System.Activities.Statements.State>kesme noktası ayarlandığında, durum ' a geçiş yapıldığında, giriş etkinlikleri veya Tetikleyicileri zamanlanmadan önce yürütme kesilir.

### <a name="BKMK_ActivityDelegates"></a>Tasarımcıda ActivityDelegate nesnelerini tanımlama ve kullanma

.NET Framework 4 ' teki etkinlikler, iş akışının diğer bölümlerinin bir iş akışının yürütmesi ile etkileşime girebildiği yürütme noktalarını ortaya çıkarmak için nesneleri <xref:System.Activities.ActivityDelegate> kullandı, ancak bu yürütme noktalarının kullanılması genellikle bir kod miktarına ihtiyaç duyulmalıdır. Bu sürümde, geliştiriciler iş akışı tasarımcısını kullanarak etkinlik temsilcileri tanımlayabilir ve kullanabilir. Daha fazla bilgi için bkz. [nasıl yapılır: iş akışı Tasarımcısı etkinlik temsilcilerini tanımlama ve kullanma](/visualstudio/workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer).

### <a name="BKMK_BuildTimeValidation"></a>Derleme zamanı doğrulaması

.NET Framework 4 ' te, iş akışı doğrulama hataları iş akışı projesinin oluşturulması sırasında derleme hatası olarak sayılmaz. Bu, iş akışı doğrulama hataları olsa bile, iş akışı projesi oluşturmanın başarılı olması anlamına gelir. .NET Framework 4,5 ' de, iş akışı doğrulama hataları yapılandırmanın başarısız olmasına neden olur.

### <a name="BKMK_DesignTimeValidation"></a>Tasarım zamanı arka plan doğrulaması

.NET Framework 4 ' te, iş akışları bir ön plan işlemi olarak doğrulanmıştı, bu da karmaşık veya zaman alan doğrulama işlemleri sırasında Kullanıcı arabirimini engelleyebilir. İş akışı doğrulaması artık bir arka plan iş parçacığında gerçekleşirken UI engellenmeyecektir.

### <a name="BKMK_ViewState"></a>XAML dosyalarında ayrı bir konumda bulunan durumu görüntüleme

.NET Framework 4 ' te, bir iş akışı için Görünüm durumu bilgileri, XAML dosyasında birçok farklı konumda depolanır. Bu, XAML 'i doğrudan okumak isteyen geliştiriciler için uygun değildir veya Görünüm durumu bilgilerini kaldırmak için kod yazın. .NET Framework 4,5 ' de, XAML dosyasındaki görünüm durumu bilgileri XAML dosyasında ayrı bir öğe olarak serileştirilir. Geliştiriciler bir etkinliğin görünüm durumu bilgilerini kolayca bulabilir ve düzenleyebilir ya da görünüm durumunu tamamen kaldırabilir.

### <a name="BKMK_ExpressionExtensibility"></a>İfade genişletilebilirliği

.NET Framework 4,5 ' de, geliştiricilerin iş akışı tasarımcısına takılmış olan kendi ifadelerini ve ifade yazma deneyimini oluşturması için bir yol sağlıyoruz.

### <a name="BKMK_BackwardCompatRehostedDesigner"></a>Yeniden barındırılan tasarımcıda Iş akışı 4,5 özellikleri için katılım

Geriye dönük uyumluluğu korumak için .NET Framework 4,5 ' de yer alan bazı yeni özellikler yeniden barındırılan tasarımcıda varsayılan olarak etkinleştirilmez. Bu, yeniden barındırılan tasarımcı kullanan mevcut uygulamaların en son sürüme güncelleştirme yaparak kesilmemesini sağlamaktır. Yeniden barındırılan tasarımcıda yeni özellikleri etkinleştirmek için, <xref:System.Activities.Presentation.DesignerConfigurationService.TargetFrameworkName%2A> ".NET Framework 4,5" olarak ayarlayın veya tek tek özellikleri etkinleştirmek için <xref:System.Activities.Presentation.DesignerConfigurationService> tek tek üyelerini ayarlayın.

## <a name="BKMK_NewWFModels"></a>Yeni Iş akışı geliştirme modelleri

Akış çizelgesi ve sıralı iş akışı geliştirme modellerine ek olarak, bu sürüm durum makinesi iş akışlarını ve sözleşme ilk iş akışı hizmetlerini içerir.

### <a name="BKMK_StateMachine"></a>Durum makinesi iş akışları

Durum makinesi iş akışları, [Microsoft .NET Framework 4 platformu güncelleştirme 1](https://blogs.msdn.microsoft.com/endpoint/2011/04/18/microsoft-net-framework-4-platform-update-1/)' de .NET Framework 4, sürüm 4.0.1 bir parçası olarak sunulmuştur. Bu güncelleştirme, geliştiricilerin durum makinesi iş akışları oluşturmalarına izin veren birkaç yeni sınıf ve etkinlik içeriyordu. Bu sınıflar ve Etkinlikler 4,5 .NET Framework güncelleştirilmiştir. Güncelleştirmeler şunları içerir:

1. Durumlar üzerinde kesme noktaları ayarlama yeteneği

2. İş akışı tasarımcısında geçişleri kopyalama ve yapıştırma özelliği

3. Paylaşılan tetikleyici geçişi oluşturma için tasarımcı desteği

4. : <xref:System.Activities.Statements.StateMachine>, <xref:System.Activities.Statements.State>ve <xref:System.Activities.Statements.Transition> dahil olmak üzere durum makinesi iş akışları oluşturmak için kullanılan etkinlikler

Aşağıdaki ekran görüntüsünde, Başlangıç [öğreticisindeki](getting-started-tutorial.md) tamamlanan durum makinesi iş akışı gösterilmektedir. [nasıl yapılır: durum makinesi iş akışı oluşturma](how-to-create-a-state-machine-workflow.md).

![Tamamlanan durum makinesi iş akışını gösteren çizim.](./media/whats-new-in-wf-in-dotnet/complete-state-machine-workflow.jpg)

Durum makinesi iş akışları oluşturma hakkında daha fazla bilgi için bkz. [durum makinesi Iş akışları](state-machine-workflows.md).

### <a name="BKMK_ContractFirst"></a>Sözleşme-ilk iş akışı geliştirme

Sözleşme-ilk iş akışı geliştirme aracı, geliştiricinin ilk olarak kodda bir sözleşme tasarlamasına olanak tanır ve ardından Visual Studio 'da birkaç tıklama ile her işlemi temsil eden araç kutusunda otomatik olarak bir etkinlik şablonu oluşturur. Bu etkinlikler daha sonra, sözleşme tarafından tanımlanan işlemleri uygulayan bir iş akışı oluşturmak için kullanılır. İş akışı Tasarımcısı, bu işlemlerin uygulandığından ve iş akışının imzasının sözleşme imzasıyla eşleştiğinden emin olmak için iş akışı hizmetini doğrular. Geliştirici, bir iş akışı hizmetini uygulanan sözleşmelerin bir koleksiyonuyla de ilişkilendirebilirler. Sözleşme-ilk iş akışı hizmeti geliştirme hakkında daha fazla bilgi için bkz. [nasıl yapılır: mevcut bir hizmet sözleşmesini tüketen iş akışı hizmeti oluşturma](how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md).
