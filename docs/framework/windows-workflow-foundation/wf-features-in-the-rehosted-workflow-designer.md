---
title: Yeniden Barındırılan İş Akışı Tasarımcısında Yeni Workflow Foundation 4.5 Özellikleri Desteği
ms.date: 03/30/2017
ms.assetid: 1a4a4038-d8e6-41dd-99ea-93bd76286772
ms.openlocfilehash: 70e4a8580a8b383bdd4e5e5299bcc5210f3210dc
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66423971"
---
# <a name="support-for-new-workflow-foundation-45-features-in-the-rehosted-workflow-designer"></a>Yeniden Barındırılan İş Akışı Tasarımcısında Yeni Workflow Foundation 4.5 Özellikleri Desteği
.NET Framework 4.5 içinde Windows Workflow Foundation'a (WF) iş akışı Tasarımcısı deneyimine yönelik bazı geliştirmeler dahil olmak üzere birçok yeni özellik kullanıma sunuldu. Bu konuda ayrıntıları: hangi bu özellikleri yeniden barındırılan tasarımcıda desteklendiği ve hangilerinin şu anda desteklenmiyor.

> [!NOTE]
>  Tasarımcı yeniden barındırma için ilgisiz olanlar dahil olmak üzere, .NET Framework 4.5 sürümünde yeni Windows Workflow Foundation (WF) özelliklerin tümünü içeren liste için bkz. [.NET 4.5 içinde Windows Workflow Foundation'daki yenilikler](whats-new-in-wf-in-dotnet.md).

## <a name="activities"></a>Etkinlikler
 Yerleşik etkinlik kitaplığı yeni etkinlikler ve mevcut etkinlikler için yeni özellikler içerir. Tüm bu yeni etkinlikleri yeniden barındırılan tasarımcıda desteklenir. Bu yeni etkinlikler hakkında daha fazla bilgi için bkz. [etkinlikleri](whats-new-in-wf-in-dotnet.md#BKMK_NewActivities) bölümünü [.NET 4.5 içinde Windows Workflow Foundation'daki yenilikler](whats-new-in-wf-in-dotnet.md).

## <a name="c-expressions"></a>C# İfadeleri
 .NET Framework 4.5 önce tüm ifadeleri iş akışlarında yalnızca Visual Basic'te yazılabilir. .NET Framework 4. 5 ', Visual Basic deyimleri yalnızca Visual Basic kullanılarak oluşturulan projeler için kullanılır. Visual C# projeleri artık C# ifadeleri için kullanın. Visual Studio 2012'de iş akışları yazmak, tam olarak işlevsel bir C# ifade Düzenleyicisi dilbilgisi vurgulama ve IntelliSense gibi hangi özellikler sağlanır. C# iş akışı projeleri Visual Basic deyimleri kullanacak önceki sürümlerinde oluşturulan çalışmaya devam eder.

> [!WARNING]
>  C# ifadelerini yeniden barındırılan tasarımcıda desteklenmez.

## <a name="new-designer-capabilities"></a>Yeni Tasarımcı özellikleri

### <a name="designer-search"></a>Tasarımcı arama
 [Hızlı Bul](whats-new-in-wf-in-dotnet.md#BKMK_QuickFind) ve [dosyalarda Bul](whats-new-in-wf-in-dotnet.md#BKMK_FindInFiles) yeniden barındırılan tasarımcıda .NET Framework 4.5 ile sunulan özellikler desteklenmez. `Toolbox` Arama yeniden barındırılan tasarımcıda desteklenir. Bu özellikler hakkında daha fazla bilgi için bkz. [Tasarımcısı arama](whats-new-in-wf-in-dotnet.md#BKMK_DesignerSearch).

> [!WARNING]
>  [Hızlı Bul](whats-new-in-wf-in-dotnet.md#BKMK_QuickFind) ve [dosyalarda Bul](whats-new-in-wf-in-dotnet.md#BKMK_FindInFiles) yeniden barındırılan tasarımcıda desteklenmez.

### <a name="delete-context-menu-item-in-variable-and-argument-designer"></a>Değişken ve bağımsız değişken Tasarımcısı'nda bağlam menüsü öğesi silme
 İçinde [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], değişkenler ve bağımsız değişkenleri yalnızca silinmesi klavyeyi kullanarak Tasarımcısı'nda. .NET Framework 4.5 ile başlayarak, değişkenler ve bağımsız değişkenler bağlam menüsü kullanılarak silinebilir. Bu özellik, yeniden barındırılan tasarımcıda desteklenir.

 Aşağıdaki ekran görüntüsünde, değişken ve bağımsız değişken Tasarımcı bağlam menüsünü gösterir.

 ![Değişken ve bağımsız değişken Tasarımcı bağlam menüsü](./media/wf-features-in-the-rehosted-workflow-designer/designer-context-menu.png)

### <a name="auto-surround-with-sequence"></a>Otomatik-çevrelemeyi dizisi
 Bir iş akışı veya belirli bir kapsayıcı etkinlikleri (gibi <xref:System.Activities.Statements.NoPersistScope>) yalnızca tek bir gövde etkinlik içerebilir, ikinci etkinlik ekleme, geliştirici ilk etkinliği silin, eklemek gerekli bir <xref:System.Activities.Statements.Sequence> etkinlik ve ardından her iki etkinlik için ekleme sıralı etkinlik. İkinci etkinlik Tasarımcı yüzeyine eklerken, .NET Framework 4.5 ile başlayarak bir `Sequence` etkinlik otomatik olarak oluşturulacak hem etkinlikleri sarmalamak için. Bu özellik, yeniden barındırılan tasarımcıda desteklenir.

 Aşağıdaki ekran görüntüsü gösterildiği bir `WriteLine` etkinliğinde `Body` , bir `NoPersistScope`.

 ![WriteLine etkinlik NoPersistScope etkinliği gövdesi.](./media/wf-features-in-the-rehosted-workflow-designer/auto-surround-write-line-activity.png)

 Aşağıdaki ekran görüntüsünde otomatik olarak oluşturulan gösterilmektedir `Sequence` etkinliğinde `Body` ikinci zaman `WriteLine` ilk düştü.

 ![Otomatik olarak oluşturulan bir sıralı bir NoPersistScope gövdesinde.](./media/wf-features-in-the-rehosted-workflow-designer/auto-surround-sequence-activity.png)

### <a name="pan-mode"></a>PAN modu
 Büyük bir iş akışı Tasarımcısı'nda daha kolay gezinme için kaydırma modu, kaydırma çubuklarını gerek kalmadan yerine geliştiricinin iş akışının görünür bölümünün taşımak için tıklayın ve sürükleyin izin vererek etkinleştirilebilir. PAN modunu etkinleştirmek için tasarımcının sağ alt köşesindeki düğmesidir. Bu özellik, yeniden barındırılan tasarımcıda desteklenir.

 Aşağıdaki ekran görüntüsünde, iş akışı Tasarımcısı alt sağ köşesinde bulunan pan düğmesini gösterir.

 ![İş Akışı Tasarımcısı'nda pan düğmesi.](./media/wf-features-in-the-rehosted-workflow-designer/pan-button-workflow-designer.png)

 Orta fare düğmesine veya Ara çubuğuna iş akışı Tasarımcısı kaydırmak için de kullanılabilir.

### <a name="multi-select"></a>Çoklu seçim
 Birden çok etkinlik, bunları (kaydırma modu etkin değilken) çevresinde bir dikdörtgen sürükleyerek veya Ctrl tuşunu basılı tutarak bir seferde seçilebilir ve istenen etkinlikleri tek tek tıklayın. Bu özellik, yeniden barındırılan tasarımcıda desteklenir.

 Birden çok etkinlik seçimleri ayrıca sürüklediğiniz ve tasarımcı içinde bırakılan ve bağlam menüsünü kullanarak da bulunulması.

### <a name="outline-view-of-workflow-items"></a>İş akışı öğelerinin anahat görünümü
 Hiyerarşik iş akışları gidin daha kolay hale getirmek için bir iş akışı bileşenleri, ağaç stili ana görünümünde gösterilir. Anahat görünümünde görüntülenen **belge anahattı** görünümü. Bu görünüm, üstteki menüden Visual Studio'da açmak için seçmeniz **görünümü**, **diğer Windows**, **belge anahattı**, ya da Ctrl W, u tuşuna basın Ana görünümünde bir düğüm tıklayarak ilgili etkinlik iş akışı tasarımcısında gider ve anahat görünümü Tasarımcısı'nda seçili etkinlikler göstermek için güncelleştirilir. Bu özellik, yeniden barındırılan tasarımcıda desteklenir.

 Aşağıdaki ekran görüntüsünde tamamlanan iş akışından [başlangıç Öğreticisi](getting-started-tutorial.md) sıralı bir iş akışı ile ana hat görünümü gösterilir.

 ![Visual Studio'da sıralı bir iş akışı ile ana hat görünümünün ekran görüntüsü](./media/wf-features-in-the-rehosted-workflow-designer/outline-view-in-workflow-designer.jpg)

### <a name="more-control-of-visibility-of-shell-bar-and-header-items"></a>Daha fazla denetim görünürlüğünü Kabuk çubuğu ve üstbilgi öğeleri
 Yeniden barındırılan tasarımcıda, bazı standart kullanıcı Arabirimi denetimleri için belirli bir iş akışı anlamı olmayabilir ve kapalı olabilir. İçinde [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], bu özelleştirme yalnızca Tasarımcısı'nın altındaki Kabuk çubuğu tarafından desteklenir. .NET Framework 4.5 olarak ayarlayarak Kabuk üstbilgi öğeleri Tasarımcı üst kısmındaki görünürlüğünü ayarlanabilir <xref:System.Activities.Presentation.View.DesignerView.WorkflowShellHeaderItemsVisibility%2A> uygun <xref:System.Activities.Presentation.View.ShellHeaderItemsVisibility> değeri.

### <a name="auto-connect-and-auto-insert-in-flowchart-and-state-machine-workflows"></a>Otomatik bağlanma ve akış ve Durum makinesi iş akışlarında otomatik Ekle
 İçinde [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], bir akış çizelgesi iş akışı düğümleri arasındaki bağlantıları el ile eklenen gerekiyordu. .NET Framework 4. 5 ', akış ve Durum makinesi düğüme sahip bir etkinlik araç kutusunu tasarımcı yüzeyine sürüklediğinizde görünür hale gelmiş noktalarını otomatik olarak bağlan. Bir etkinlik otomatik olarak bu noktalarından birine bırakarak, gerekli bağlantı birlikte etkinlik ekler.

 Aşağıdaki ekran görüntüsünde bir etkinlik araç kutusundan sürüklendiğinde görünür hale gelmiş eki noktalarını gösterir.

 ![Akış başlangıç düğümü gösteren otomatik bağlanma noktası](./media/wf-features-in-the-rehosted-workflow-designer/auto-connect-points-start-node.png)

 Etkinlikler de akış düğüm ve düğüm iki düğüm arasındaki otomatik olarak eklemek üzere durumları arasında bağlantılar sürüklenebilen. Aşağıdaki ekran görüntüsünde vurgulanan bağlantı satırı burada etkinlikler araç kutusundan sürüklediğiniz ve olması bırakılan gösterir.

 ![Etkinlikleri silmek için tanıtıcı otomatik Ekle](./media/wf-features-in-the-rehosted-workflow-designer/auto-insert-connecting-line.png)

 Otomatik olarak bağlanabilir ve otomatik ekleme, yeniden barındırılan tasarımcıda desteklenir.

### <a name="designer-annotations"></a>Tasarımcı ek açıklamaları
 Daha büyük iş akışları geliştirme kolaylaştırmak için tasarımcı tasarım süreci izlemenize yardımcı olması için ekleme ek açıklamalarını destekler. Ek açıklama, etkinlikleri, durumları, akış düğümleri, değişkenler ve bağımsız değişkenler eklenebilir. Aşağıdaki ekran görüntüsünde, ek açıklamalar tasarımcıya eklemek için kullanılan bağlam menüsünü gösterir.

 ![Gösterimler ekleme menüsü gösteren ekran görüntüsü.](./media/wf-features-in-the-rehosted-workflow-designer/designer-annotations-context-menu.png)

 Tasarımcı ek açıklamaları yeniden barındırılan tasarımcıda desteklenir.

### <a name="define-and-consume-activitydelegate-objects-in-the-designer"></a>Tanımlama ve tasarımcıda ActivityDelegate nesneleri kullanma
 Etkinlikler [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] kullanılan <xref:System.Activities.ActivityDelegate> burada diğer bölümlerini bir iş akışı ile bir iş akışının yürütme destekliyordu, ancak bu yürütme noktaları genellikle kullanarak gerekli ciddi miktarda bir kod yürütme noktaları ortaya çıkarmak için nesne. Bu sürümde, geliştiricilerin tanımlayabilir ve iş akışı Tasarımcısı kullanarak etkinlik temsilcileri kullanma. Daha fazla bilgi için [nasıl yapılır: Tanımlama ve iş akışı tasarımcısında etkinlik temsilcileri kullanma](/visualstudio/workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer).

 Etkinlik temsilcileri yeniden barındırılan tasarımcıda desteklenir.

### <a name="build-time-validation"></a>Derleme zamanı doğrulama
 İçinde [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], iş akışı doğrulama hataları iş akışı projesi derleme sırasında derleme hataları sayılan olmayan. Bu, bir iş akışı oluşturma geliyordu bile iş akışı doğrulama hatalarını zamanki proje başarılı. .NET Framework 4. 5 ', başarısız için yapı iş akışı doğrulama hatalarına neden.

> [!WARNING]
>  Derleme zamanı doğrulama yeniden barındırılan tasarımcıda desteklenmez.  
  
### <a name="design-time-background-validation"></a>Tasarım zamanı arka plan doğrulama  
 İçinde [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], iş akışları karmaşık ya da zaman harcayan doğrulama işlemi sırasında kullanıcı Arabirimi olası engelleyebilecek bir ön plan işlemi olarak doğrulandı. Böylece kullanıcı Arabirimi engellenmez artık iş akışı doğrulamasındaki bir arka plan iş parçacığı üzerinde gerçekleşir.  
  
 Tasarım zamanı arka plan doğrulama yeniden barındırılan tasarımcıda desteklenir.  
  
### <a name="view-state-located-in-a-separate-location-in-xaml-files"></a>XAML dosyaları ayrı bir konumda bulunan görünüm durumu  
 İçinde [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], bir iş akışı için Görünüm durumu bilgilerini arasında birçok farklı konumlara XAML dosyasında depolanır. Bu, doğrudan XAML okuma veya Görünüm durumu bilgilerini kaldırmak için kod yazma isteyen geliştiriciler için kullanışsız olur. .NET Framework 4.5 içinde ilişkin görünüm durumu bilgilerinin XAML dosyasında bir XAML dosyasında ayrı bir öğe olarak seri hale getirilir.  Kolayca geliştiriciler bulun ve etkinliğin görünüm durumu bilgilerini düzenlemek veya Görünüm durumu tamamen kaldırabilirsiniz.  
  
 Bu özellik, yeniden barındırılan iş akışı Tasarımcısı'nda desteklenir.  
  
### <a name="opt-in-for-workflow-45-features-in-rehosted-designer"></a>İş akışı 4.5 özellikleri yeniden barındırılan tasarımcıda katılımı  
 Geriye dönük uyumluluğu korumak için bazı yeni özellikler .NET Framework 4.5 yeniden barındırılan tasarımcıda varsayılan olarak etkin değildir. Bu yeniden barındırılan Tasarımcısı'nı kullanan mevcut uygulamaları en son sürüme güncelleştirerek etkilenmemesini sağlamak içindir. Yeniden barındırılan tasarımcıda yeni özellikleri etkinleştirmek için ya da ayarlayın <xref:System.Activities.Presentation.DesignerConfigurationService.TargetFrameworkName%2A> için ".Net Framework 4.5", veya tek tek üyeleri <xref:System.Activities.Presentation.DesignerConfigurationService> tek tek özellikleri etkinleştirmek için.  
  
## <a name="new-workflow-development-models"></a>Yeni iş akışı geliştirme modelleri  
 Bu sürüm, akış ve sıralı iş akışı geliştirme modelleri ek olarak, durum makine iş akışları ve sözleşme öncelikli iş akışı hizmetleri içerir.  
  
### <a name="state-machine-workflows"></a>Durum makinesi iş akışları  
 Durum makinesi iş akışları, .NET Framework 4.0.1'in parçası olarak sunulmuştur [Microsoft .NET Framework 4 Platform Update 1](https://go.microsoft.com/fwlink/?LinkID=215092). Bu, birkaç yeni sınıfı ve geliştiricilerin durum makine iş akışları oluşturmak izin verilen etkinlikleri güncelleştirmenin. Bu sınıflar ve etkinlikler, .NET Framework 4.5 için güncelleştirilmiştir. Güncelleştirmeler şunları içerir:  
  
1. Durumlar üzerinde kesme noktaları ayarlama olanağı  
  
2. İş akışı tasarımcısında geçişleri yapıştırın olanağı  
  
3. Paylaşılan tetikleyici geçişi oluşumu için tasarımcı desteği  
  
4. Etkinlikler dahil olmak üzere durum makine iş akışları oluşturmak için kullanılan: <xref:System.Activities.Statements.StateMachine>, <xref:System.Activities.Statements.State>, ve <xref:System.Activities.Statements.Transition>  
  
 Aşağıdaki ekran görüntüsünde tamamlanan durum makine iş akışından gösterilmektedir [başlangıç Öğreticisi](getting-started-tutorial.md) adım [nasıl yapılır: Bir Durum makinesi iş akışı oluşturmak](how-to-create-a-state-machine-workflow.md).  
  
 ![Tamamlanan Durum makinesi iş akışı gösteren şekil.](./media/wf-features-in-the-rehosted-workflow-designer/complete-state-machine-workflow.jpg)  
  
 Durum makine iş akışları oluşturma hakkında daha fazla bilgi için bkz. [durum makine iş akışları](state-machine-workflows.md). Durum makinesi iş akışı yeniden barındırılan tasarımcıda desteklenir.  
  
### <a name="contract-first-workflow-development"></a>Sözleşme öncelikli iş akışı geliştirme  
 Bir kod sözleşmesi ilk tasarlayın ve ardından Visual Studio'da birkaç tıklama ile her bir işlemi temsil eden araç kutusunda otomatik olarak bir etkinlik şablonu oluşturmak Geliştirici sözleşme öncelikli iş akışı geliştirme aracı sağlar. Bu etkinlikler, ardından anlaşmada tanımlanan işlemleri uygulayan bir iş akışı oluşturmak için kullanılır. İş Akışı Tasarımcısı bu işlemleri uygulanır ve iş akışı imzası sözleşme imzayla eşleşen emin olmak için iş akışı hizmeti doğrular. Geliştirici, ayrıca bir iş akışı hizmeti uygulanan sözleşmelerin koleksiyonu ile ilişkilendirebilirsiniz. Sözleşme öncelikli iş akışı hizmet geliştirme hakkında daha fazla bilgi için bkz. [nasıl yapılır: Mevcut bir hizmet anlaşmasını kullanan iş akışı hizmeti oluşturma](how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md).  
  
> [!WARNING]
>  Sözleşme öncelikli iş akışı geliştirme iş akışı Tasarımcısı'nda desteklenmiyor.
