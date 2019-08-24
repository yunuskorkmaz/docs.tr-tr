---
title: Yeniden Barındırılan İş Akışı Tasarımcısında Yeni Workflow Foundation 4.5 Özellikleri Desteği
ms.date: 03/30/2017
ms.assetid: 1a4a4038-d8e6-41dd-99ea-93bd76286772
ms.openlocfilehash: 20623c8d2f6bf66d2668fd07b0acae67865a3235
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69987229"
---
# <a name="support-for-new-workflow-foundation-45-features-in-the-rehosted-workflow-designer"></a>Yeniden Barındırılan İş Akışı Tasarımcısında Yeni Workflow Foundation 4.5 Özellikleri Desteği
.NET Framework 4,5 ' de Windows Workflow Foundation (WF), iş akışı Tasarımcısı deneyimine yönelik çeşitli geliştirmeler de dahil olmak üzere birçok yeni özellik sunmuştur. Bu konu başlığı altında, yeniden barındırılan Tasarımcıda Bu özelliklerden hangilerinin desteklendiği ve hangilerinin Şu anda desteklenmeyen ayrıntıları verilmektedir.

> [!NOTE]
> Tasarımcı yeniden barındırma ile ilgili olanlar da dahil olmak üzere .NET Framework 4,5 ' de tanıtılan tüm yeni Windows Workflow Foundation (WF) özelliklerinin bir listesi için bkz. [.net 4,5](whats-new-in-wf-in-dotnet.md)' de Windows Workflow Foundation yenilikleri.

## <a name="activities"></a>Etkinlikler
 Yerleşik etkinlik kitaplığı, yeni etkinlikler ve mevcut etkinliklere yönelik yeni özellikler içerir. Bu yeni etkinliklerin hepsi yeniden barındırılan tasarımcıda desteklenir. Bu yeni etkinlikler hakkında daha fazla bilgi için, [.net 4,5 'deki Windows Workflow Foundation](whats-new-in-wf-in-dotnet.md)yenilikleri bölümüne bakın. [](whats-new-in-wf-in-dotnet.md#BKMK_NewActivities)

## <a name="c-expressions"></a>C# İfadeleri
 .NET Framework 4,5 ' dan önce, iş akışlarındaki tüm ifadeler yalnızca Visual Basic yazdırılabilir. .NET Framework 4,5 ' de Visual Basic ifadeler yalnızca Visual Basic kullanılarak oluşturulan projeler için kullanılır. Artık C# Visual projeleri ifadeler C# için kullanılır. Visual Studio 2012 ' de iş akışları yazarken, tam işlevli C# bir ifade düzenleyicisine, dilbilgisi vurgulama ve IntelliSense gibi yetenekler sağlanır. C#önceki sürümlerde oluşturulan Visual Basic ifadeleri kullanan iş akışı projeleri çalışmaya devam edecektir.

> [!WARNING]
> C#yeniden barındırılan tasarımcıda ifadeler desteklenmez.

## <a name="new-designer-capabilities"></a>Yeni tasarımcı özellikleri

### <a name="designer-search"></a>Tasarımcı arama
 .NET Framework 4,5 ile tanıtılan [dosyalardaki](whats-new-in-wf-in-dotnet.md#BKMK_FindInFiles) [hızlı bul](whats-new-in-wf-in-dotnet.md#BKMK_QuickFind) ve bul özellikleri yeniden barındırılan tasarımcıda desteklenmez. Arama `Toolbox` , yeniden barındırılan tasarımcıda desteklenir. Bu özellikler hakkında daha fazla bilgi için bkz. [Tasarımcı arama](whats-new-in-wf-in-dotnet.md#BKMK_DesignerSearch).

> [!WARNING]
> Yeniden barındırılan tasarımcıda [dosyalarda](whats-new-in-wf-in-dotnet.md#BKMK_FindInFiles) [hızlı bulma](whats-new-in-wf-in-dotnet.md#BKMK_QuickFind) ve bulma desteklenmez.

### <a name="delete-context-menu-item-in-variable-and-argument-designer"></a>Değişken ve bağımsız değişken tasarımcısında bağlam menüsü öğesini Sil
 ' [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)]De, değişkenler ve bağımsız değişkenler yalnızca klavye kullanılarak tasarımcıda silinebilir. .NET Framework 4,5 ' den başlayarak, değişkenler ve bağımsız değişkenler bağlam menüsü kullanılarak silinebilir. Bu özellik, yeniden barındırılan tasarımcıda desteklenir.

 Aşağıdaki ekran görüntüsünde, değişken ve bağımsız değişken tasarımcı bağlam menüsü gösterilmektedir.

 ![Değişken ve bağımsız değişken Tasarımcısı bağlam menüsü](./media/wf-features-in-the-rehosted-workflow-designer/designer-context-menu.png)

### <a name="auto-surround-with-sequence"></a>Sırayla Otomatik sarma
 Bir iş akışı veya bazı kapsayıcı Etkinlikleri (gibi <xref:System.Activities.Statements.NoPersistScope>) yalnızca tek bir gövde etkinliği içerebildiği için, ikinci bir etkinlik eklemek geliştiricinin ilk etkinliği silmesi, bir <xref:System.Activities.Statements.Sequence> etkinlik eklemesi ve ardından her iki etkinliği de sıra etkinliği. .NET Framework 4,5 ' den başlayarak, tasarımcı yüzeyine ikinci bir etkinlik eklenirken her iki etkinliği de `Sequence` kaydırmak için bir etkinlik otomatik olarak oluşturulur. Bu özellik, yeniden barındırılan tasarımcıda desteklenir.

 Aşağıdaki ekran görüntüsünde `Body` içindeki bir `WriteLine` `NoPersistScope`etkinlik gösterilmektedir.

 ![NoPersistScope etkinliğinin gövdesinde bir WriteLine etkinliği.](./media/wf-features-in-the-rehosted-workflow-designer/auto-surround-write-line-activity.png)

 Aşağıdaki ekran görüntüsünde, `Sequence` `Body` birincinin altına ikinci `WriteLine` kez bırakıldığında otomatik olarak oluşturulan etkinlik gösterilmektedir.

 ![NoPersistScope gövdesinde otomatik olarak oluşturulan bir sıra.](./media/wf-features-in-the-rehosted-workflow-designer/auto-surround-sequence-activity.png)

### <a name="pan-mode"></a>Kaydırma modu
 Tasarımcıda büyük bir iş akışında daha kolay gezinmek için, kaydırma modu etkinleştirilebilir, böylece Geliştirici, kaydırma çubuklarının kullanılmasına gerek kalmadan iş akışının görünür kısmını taşımak için tıklamasına ve sürüklemesine olanak tanır. Yatay kaydırma modunu etkinleştirmek için düğme, tasarımcının sağ alt köşesindedir. Bu özellik, yeniden barındırılan tasarımcıda desteklenir.

 Aşağıdaki ekran görüntüsünde, iş akışı tasarımcısının sağ alt köşesinde bulunan kaydır düğmesi gösterilmektedir.

 ![İş akışı tasarımcısında kaydırma düğmesi vurgulandı.](./media/wf-features-in-the-rehosted-workflow-designer/pan-button-workflow-designer.png)

 Orta fare düğmesi veya boşluk çubuğu, iş akışı tasarımcısını kaydırmak için de kullanılabilir.

### <a name="multi-select"></a>Çoklu seçim
 Birden çok etkinlik tek seferde seçilebilir (kaydırma modu etkin değil), ya da CTRL tuşunu basılı tutarak istenen etkinliklere tek tek tıklayarak seçebilirsiniz. Bu özellik, yeniden barındırılan tasarımcıda desteklenir.

 Birden çok etkinlik seçimi de tasarımcı içinde sürüklenip bırakılabilir ve bağlam menüsü kullanılarak da etkileşim edilebilir.

### <a name="outline-view-of-workflow-items"></a>İş akışı öğelerinin Ana Hat görünümü
 Hiyerarşik iş akışlarının gezinmesinin daha kolay olmasını sağlamak için bir iş akışının bileşenleri ağaç stili bir anahat görünümünde gösterilir. Ana hat görünümü **Belge anahat** görünümünde görüntülenir. Visual Studio 'da bu görünümü açmak için, üstteki menüden **Görünüm**, **diğer pencereler**, **Belge Anahattı**' nı seçin veya CTRL W, U tuşlarına basın. Ana hat görünümündeki bir düğüme tıkladığınızda, iş akışı tasarımcısında ilgili etkinliğe gidebilirsiniz ve ana hat görünümü tasarımcıda seçilen etkinlikleri gösterecek şekilde güncelleştirilir. Bu özellik, yeniden barındırılan tasarımcıda desteklenir.

 Başlangıç [öğreticisindeki](getting-started-tutorial.md) tamamlanan iş akışının aşağıdaki ekran görüntüsü, sıralı bir iş akışı ile ana hat görünümünü gösterir.

 ![Visual Studio 'da sıralı iş akışı ile ana hat görünümünün ekran görüntüsü](./media/wf-features-in-the-rehosted-workflow-designer/outline-view-in-workflow-designer.jpg)

### <a name="more-control-of-visibility-of-shell-bar-and-header-items"></a>Kabuk çubuğu ve üst bilgi öğelerinin görünürlüğü hakkında daha fazla denetim
 Yeniden barındırılan bir tasarımcıda, bazı standart Kullanıcı arabirimi denetimlerinin belirli bir iş akışı için anlamı olmayabilir ve kapatılabilir. ' [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)]De, bu özelleştirme yalnızca Tasarımcı 'nın altındaki Kabuk çubuğu tarafından desteklenir. .NET Framework 4,5 ' de, tasarımcı 'nın en üstündeki kabuk üst bilgi öğelerinin görünürlüğü uygun <xref:System.Activities.Presentation.View.DesignerView.WorkflowShellHeaderItemsVisibility%2A> <xref:System.Activities.Presentation.View.ShellHeaderItemsVisibility> değerle ayarlanarak ayarlanabilir.

### <a name="auto-connect-and-auto-insert-in-flowchart-and-state-machine-workflows"></a>Akış Çizelgesine ve durum makinesi iş akışlarına otomatik bağlan ve otomatik ekle
 ' [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)]De, bir akış çizelgesi iş akışında düğümler arasındaki bağlantıların el ile eklenmesi gerekiyordu. .NET Framework 4,5 ' de, akış çizelgesi ve durum makinesi düğümlerinde, bir etkinlik araç kutusundan tasarımcı yüzeyine sürüklendiğinde görünür hale gelen otomatik bağlantı noktaları bulunur. Bu noktaların birine bir etkinliğin atılması, etkinliği gereken bağlantıyla birlikte otomatik olarak ekler.

 Aşağıdaki ekran görüntüsünde, bir etkinlik araç kutusundan sürüklendiğinde görünür hale gelen ek noktaları gösterilmektedir.

 ![Akış çizelgesi başlangıç düğümü otomatik bağlantı noktalarını gösterir](./media/wf-features-in-the-rehosted-workflow-designer/auto-connect-points-start-node.png)

 Ayrıca, iki düğüm arasında düğümü otomatik olarak eklemek için, aynı zamanda akış çizelgesi düğümleri ve durumlar arasındaki bağlantılar üzerinde de değiştirilebilir. Aşağıdaki ekran görüntüsünde, etkinliklerin araç kutusundan sürüklenip bırakılbileceği vurgulanan bağlantı çizgisi gösterilmektedir.

 ![Bırakma etkinlikleri için otomatik ekleme tutamacı](./media/wf-features-in-the-rehosted-workflow-designer/auto-insert-connecting-line.png)

 Yeniden barındırılan tasarımcıda otomatik bağlanma ve otomatik ekleme desteklenir.

### <a name="designer-annotations"></a>Tasarımcı ek açıklamaları
 Daha büyük iş akışlarının geliştirilmesini kolaylaştırmak için, tasarımcı artık tasarım sürecini izlemeye yardımcı olan ek açıklamalar eklemeyi desteklemektedir. Ek açıklama, etkinliklere, durumlara, akış çizelgesi düğümlerine, değişkenlere ve bağımsız değişkenlere eklenebilir. Aşağıdaki ekran görüntüsünde, tasarımcıya ek açıklamalar eklemek için kullanılan bağlam menüsü gösterilmektedir.

 ![Gösterimler ekleme menüsünü gösteren ekran görüntüsü.](./media/wf-features-in-the-rehosted-workflow-designer/designer-annotations-context-menu.png)

 Tasarımcı ek açıklamaları yeniden barındırılan tasarımcıda desteklenir.

### <a name="define-and-consume-activitydelegate-objects-in-the-designer"></a>Tasarımcıda ActivityDelegate nesnelerini tanımlama ve kullanma
 İş akışının diğer <xref:System.Activities.ActivityDelegate> bölümlerinin bir iş akışının yürütülmesine etkileşime girebildiği, ancak bu yürütme noktalarının kullanılması, genellikle bir kod miktarına ihtiyaç duyduğu yürütme noktalarını ortaya çıkarmak için kullanılannesnelerdekietkinliklerdir.[!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] Bu sürümde, geliştiriciler iş akışı tasarımcısını kullanarak etkinlik temsilcileri tanımlayabilir ve kullanabilir. Daha fazla bilgi için [nasıl yapılır: İş Akışı Tasarımcısı](/visualstudio/workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer)etkinlik temsilcilerini tanımlayın ve kullanın.

 Etkinlik temsilcileri yeniden barındırılan tasarımcıda desteklenir.

### <a name="build-time-validation"></a>Derleme zamanı doğrulaması
 ' [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)]De iş akışı doğrulama hataları, iş akışı projesinin oluşturulması sırasında derleme hatası olarak sayılmaz. Bu, iş akışı doğrulama hataları olsa bile, iş akışı projesi oluşturmanın başarılı olması anlamına gelir. .NET Framework 4,5 ' de, iş akışı doğrulama hataları yapılandırmanın başarısız olmasına neden olur.

> [!WARNING]
> Yeniden barındırılan tasarımcıda derleme zamanı doğrulaması desteklenmez.  
  
### <a name="design-time-background-validation"></a>Tasarım zamanı arka plan doğrulaması  
 ' [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)]De, iş akışları bir ön plan işlemi olarak doğrulanmıştı, bu da karmaşık veya zaman alıcı doğrulama işlemleri sırasında Kullanıcı arabirimini engelleyebilir. İş akışı doğrulaması artık bir arka plan iş parçacığında gerçekleşirken UI engellenmeyecektir.  
  
 Yeniden barındırılan tasarımcıda tasarım zamanı arka plan doğrulaması desteklenir.  
  
### <a name="view-state-located-in-a-separate-location-in-xaml-files"></a>XAML dosyalarında ayrı bir konumda bulunan durumu görüntüleme  
 ' [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)]De, bir iş akışı için Görünüm durumu bilgileri, xaml dosyasında birçok farklı konumda depolanır. Bu, XAML 'i doğrudan okumak isteyen geliştiriciler için uygun değildir veya Görünüm durumu bilgilerini kaldırmak için kod yazın. .NET Framework 4,5 ' de, XAML dosyasındaki görünüm durumu bilgileri XAML dosyasında ayrı bir öğe olarak serileştirilir.  Geliştiriciler bir etkinliğin görünüm durumu bilgilerini kolayca bulabilir ve düzenleyebilir ya da görünüm durumunu tamamen kaldırabilir.  
  
 Bu özellik, yeniden barındırılan iş akışı tasarımcısında desteklenir.  
  
### <a name="opt-in-for-workflow-45-features-in-rehosted-designer"></a>Yeniden barındırılan tasarımcıda Iş akışı 4,5 özellikleri için katılım  
 Geriye dönük uyumluluğu korumak için .NET Framework 4,5 ' de yer alan bazı yeni özellikler yeniden barındırılan tasarımcıda varsayılan olarak etkinleştirilmez. Bu, yeniden barındırılan tasarımcı kullanan mevcut uygulamaların en son sürüme güncelleştirme yaparak kesilmemesini sağlamaktır. Yeniden barındırılan tasarımcıda yeni özellikleri etkinleştirmek için, ".NET Framework 4,5 <xref:System.Activities.Presentation.DesignerConfigurationService.TargetFrameworkName%2A> " olarak ayarlayın veya ayrı ayrı özellikleri etkinleştirmek <xref:System.Activities.Presentation.DesignerConfigurationService> için ayrı ayrı üyeleri ayarlayın.  
  
## <a name="new-workflow-development-models"></a>Yeni Iş akışı geliştirme modelleri  
 Akış çizelgesi ve sıralı iş akışı geliştirme modellerine ek olarak, bu sürüm durum makinesi iş akışlarını ve sözleşme ilk iş akışı hizmetlerini içerir.  
  
### <a name="state-machine-workflows"></a>Durum makinesi iş akışları  
 Durum makinesi iş akışları, [Microsoft .NET Framework 4 Platform Güncelleştirme 1](https://go.microsoft.com/fwlink/?LinkID=215092)' de .NET Framework 4.0.1 bir parçası olarak sunulmuştur. Bu güncelleştirme, geliştiricilerin durum makinesi iş akışları oluşturmalarına izin veren birkaç yeni sınıf ve etkinlik içeriyordu. Bu sınıflar ve Etkinlikler 4,5 .NET Framework güncelleştirilmiştir. Güncelleştirmeler şunları içerir:  
  
1. Durumlar üzerinde kesme noktaları ayarlama yeteneği  
  
2. İş akışı tasarımcısında geçişleri kopyalama ve yapıştırma özelliği  
  
3. Paylaşılan tetikleyici geçişi oluşturma için tasarımcı desteği  
  
4. Aşağıdakiler dahil olmak üzere durum makine iş akışları oluşturmak için <xref:System.Activities.Statements.StateMachine>kullanılan <xref:System.Activities.Statements.State>Etkinlikler:, ve<xref:System.Activities.Statements.Transition>  
  
 Aşağıdaki ekran görüntüsünde, Başlangıç [öğreticisinde tamamlanan durum makinesi iş [](getting-started-tutorial.md) akışı gösterilmektedir. Bir durum makinesi Iş akışı](how-to-create-a-state-machine-workflow.md)oluşturun.  
  
 ![Tamamlanan durum makinesi iş akışını gösteren çizim.](./media/wf-features-in-the-rehosted-workflow-designer/complete-state-machine-workflow.jpg)  
  
 Durum makinesi iş akışları oluşturma hakkında daha fazla bilgi için bkz. [durum makinesi Iş akışları](state-machine-workflows.md). Durum makinesi iş akışları, yeniden barındırılan tasarımcıda desteklenir.  
  
### <a name="contract-first-workflow-development"></a>Sözleşme-ilk iş akışı geliştirme  
 Sözleşme-ilk iş akışı geliştirme aracı, geliştiricinin ilk olarak kodda bir sözleşme tasarlamasına olanak tanır ve ardından Visual Studio 'da birkaç tıklama ile her işlemi temsil eden araç kutusunda otomatik olarak bir etkinlik şablonu oluşturur. Bu etkinlikler daha sonra, sözleşme tarafından tanımlanan işlemleri uygulayan bir iş akışı oluşturmak için kullanılır. İş akışı Tasarımcısı, bu işlemlerin uygulandığından ve iş akışının imzasının sözleşme imzasıyla eşleştiğinden emin olmak için iş akışı hizmetini doğrular. Geliştirici, bir iş akışı hizmetini uygulanan sözleşmelerin bir koleksiyonuyla de ilişkilendirebilirler. Sözleşme-ilk iş akışı hizmeti geliştirme hakkında daha fazla bilgi için [bkz. nasıl yapılır: Mevcut bir hizmet sözleşmesini](how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md)tüketen bir iş akışı hizmeti oluşturun.  
  
> [!WARNING]
> Sözleşme-ilk iş akışı geliştirme iş akışı tasarımcısında desteklenmez.
