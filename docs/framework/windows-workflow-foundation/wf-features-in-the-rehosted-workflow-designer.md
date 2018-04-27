---
title: Rehosted iş akışı Tasarımcısı'nda yeni iş akışı Foundation 4.5 özellikleri için destek
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1a4a4038-d8e6-41dd-99ea-93bd76286772
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 999c18f20264a71cf73bbd5afd352ad3104a03e8
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="support-for-new-workflow-foundation-45-features-in-the-rehosted-workflow-designer"></a>Rehosted iş akışı Tasarımcısı'nda yeni iş akışı Foundation 4.5 özellikleri için destek
[!INCLUDE[wf](../../../includes/wf-md.md)] içinde [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] iş akışı Tasarımcısı deneyimi bazı geliştirmeler dahil olmak üzere birçok yeni özellik sunulmuştur. Bu konu, bu özelliklerin rehosted Tasarımcısı'nda desteklenen ve hangilerinin şu anda desteklenmiyor ayrıntıları.  
  
> [!NOTE]
>  Tüm yeni bir listesi için [!INCLUDE[wf](../../../includes/wf-md.md)] özellikleri kullanıma sunulan [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], olanlar dahil olmak üzere ilgisiz Tasarımcı yeniden barındırma için, bkz: [.NET 4.5, Windows Workflow Foundation yenilikler](../../../docs/framework/windows-workflow-foundation/whats-new-in-wf-in-dotnet.md).  
  
## <a name="activities"></a>Etkinlikler  
 Yerleşik etkinlik kitaplığı yeni etkinlikler ve varolan etkinlikleri için yeni özellikler içerir. Bu yeni etkinliklerin tümü rehosted Tasarımcısı'nda desteklenir. Bu yeni etkinlikler hakkında daha fazla bilgi için bkz: [etkinlikleri](../../../docs/framework/windows-workflow-foundation/whats-new-in-wf-in-dotnet.md#BKMK_NewActivities) bölümünü [.NET 4.5, Windows Workflow Foundation yenilikler](../../../docs/framework/windows-workflow-foundation/whats-new-in-wf-in-dotnet.md).  
  
## <a name="c-expressions"></a>C# ifadeleri  
 Öncesinde [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], tüm ifadeleri iş akışlarında yalnızca Visual Basic'te yazılmış. İçinde [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], Visual Basic ifadeleri yalnızca Visual Basic kullanılarak oluşturulan projeleri için kullanılır. Visual C# projeleri şimdi C# ifadeler için kullanın. İş akışlarında yazarken [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)], tam olarak işlevsel bir C# ifade Düzenleyicisi dilbilgisi vurgulama ve IntelliSense gibi hangi özellikleri sağlanır. Visual Basic ifadeleri kullanan önceki sürümlerde oluşturulan C# projeleri iş akışı çalışmaya devam eder.  
  
> [!WARNING]
>  C# ifadeleri rehosted Tasarımcısı'nda desteklenmez.  
  
## <a name="new-designer-capabilities"></a>Yeni Tasarımcısı özellikleri  
  
### <a name="designer-search"></a>Tasarımcı arama  
 [Hızlı Bul'u](../../../docs/framework/windows-workflow-foundation/whats-new-in-wf-in-dotnet.md#BKMK_QuickFind) ve [dosyalarda Bul](../../../docs/framework/windows-workflow-foundation/whats-new-in-wf-in-dotnet.md#BKMK_FindInFiles) ile sunulan özellikler [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] rehosted Tasarımcısı'nda desteklenmez. `Toolbox` Arama rehosted Tasarımcısı'nda desteklenir. Bu özellikler hakkında daha fazla bilgi için bkz: [Tasarımcısı arama](../../../docs/framework/windows-workflow-foundation/whats-new-in-wf-in-dotnet.md#BKMK_DesignerSearch).  
  
> [!WARNING]
>  [Hızlı Bul](../../../docs/framework/windows-workflow-foundation/whats-new-in-wf-in-dotnet.md#BKMK_QuickFind) ve [dosyalarda Bul](../../../docs/framework/windows-workflow-foundation/whats-new-in-wf-in-dotnet.md#BKMK_FindInFiles) rehosted Tasarımcısı'nda desteklenmez.  
  
### <a name="delete-context-menu-item-in-variable-and-argument-designer"></a>Değişkeni ve bağımsız değişkeni Tasarımcısı'nda bağlam menüsü öğesini sil  
 İçinde [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], değişkenler ve bağımsız değişkenler yalnızca silinmesi için klavyeyi kullanma Tasarımcısı'nda. İle başlayarak [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], değişkenler ve bağımsız değişkenler bağlam menüsünü kullanarak silinebilir. Bu özellik rehosted Tasarımcısı'nda desteklenir.  
  
 Aşağıdaki ekran görüntüsünde değişkeni ve bağımsız değişkeni Tasarımcı bağlam menüsünü gösterir.  
  
 ![Değişken bağımsız değişken Tasarımcı bağlam menüsünü](../../../docs/framework/windows-workflow-foundation/media/designercontextmenu.png "DesignerContextMenu")  
  
### <a name="auto-surround-with-sequence"></a>Otomatik surround sırası  
 Bir iş akışı veya belirli kapsayıcı etkinlikleri bu yana (gibi <xref:System.Activities.Statements.NoPersistScope>) yalnızca bir tek gövde etkinlik içerebilir, ikinci bir etkinlik ekleme, ilk etkinlik silmek için add Geliştirici gerekli bir <xref:System.Activities.Statements.Sequence> etkinliği ve her iki etkinlikler ekleme sıralı etkinlik. İle başlayarak [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], ikinci bir etkinlik Tasarımcı yüzeyine eklerken bir `Sequence` etkinlik otomatik olarak oluşturulacak hem etkinlikleri sarmalamak için. Bu özellik rehosted Tasarımcısı'nda desteklenir.  
  
 Aşağıdaki ekran görüntüsü gösterildiği bir `WriteLine` etkinliğinde `Body` , bir `NoPersistScope`.  
  
 ![Otomatik&#45;çevreleyen bırakma konumu](../../../docs/framework/windows-workflow-foundation/media/autosurround1.png "AutoSurround1")  
  
 Aşağıdaki ekran görüntüsü otomatik olarak oluşturulan gösterir `Sequence` etkinliğinde `Body` ikinci bir zaman `WriteLine` ilk bırakılır.  
  
 ![Sıralı etkinlik otomatik olarak oluşturulan](../../../docs/framework/windows-workflow-foundation/media/autosurround2.png "AutoSurround2")  
  
### <a name="pan-mode"></a>Yatay kaydırma modu  
 Daha kolay büyük bir iş akışı Tasarımcısı'nda gitmek için kaydırma modu, kaydırma çubuklarını kullanın gerek yerine geliştiricinin iş akışı görünen dilimini taşımak için tıklatın ve sürükleyin izin vererek etkinleştirilebilir. PAN modunu etkinleştirmek için düğmesi Designer sağ alt köşesindeki değildir. Bu özellik rehosted Tasarımcısı'nda desteklenir.  
  
 Aşağıdaki ekran görüntüsünde iş akışı Tasarımcısı'nı alt sağ köşesinde bulunan pan düğmesini gösterir.  
  
 ![İş Akışı Tasarımcısı'nda PAN düğmesi](../../../docs/framework/windows-workflow-foundation/media/panbutton.png "PanButton")  
  
 Orta fare düğmesini veya Ara çubuğu iş akışı Tasarımcısı'nı kaydırmak için de kullanılabilir.  
  
### <a name="multi-select"></a>Çoklu seçim  
 Birden çok etkinliği aynı anda bunları (kaydırma modu etkinleştirilmediğinde) çevresinde bir dikdörtgen sürükleyerek veya Ctrl tuşunu basılı tutarak seçilebilir ve istenen etkinlikleri tek tek tıklatın. Bu özellik rehosted Tasarımcısı'nda desteklenir.  
  
 Birden çok etkinlik seçimin ayrıca sürüklenen ve Tasarımcısı'nda bırakılan ve bağlam menüsünü kullanarak da bulunulması.  
  
### <a name="outline-view-of-workflow-items"></a>İş akışı öğelerinin anahat görünümü  
 Hiyerarşik iş akışları gitmek kolaylaştırmak için bir iş akışının bileşenleri bir ağaç stili anahat görünümünde gösterilir. Anahat görünümünde görüntülenen **belge anahattı** görünümü. Bu görünüm, üstteki menüden Visual Studio'da açın, seçin **Görünüm**, **diğer pencereler**, **belge anahattı**, veya Ctrl W, u tuşlarına basın Anahat görünümünde bir düğümüne tıklayarak karşılık gelen etkinlik iş akışı Tasarımcısı'nda gider ve anahat görünümü Tasarımcısı'nda seçili etkinlikler göstermek için güncelleştirilmiştir. Bu özellik rehosted Tasarımcısı'nda desteklenir.  
  
 Aşağıdaki ekran görüntüsünde tamamlanan iş akışını [başlangıç Öğreticisi](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md) sıralı iş akışı ile anahat görünümü gösterir.  
  
 ![Anahat görünümü iş akışı Tasarımcısı'nda](../../../docs/framework/windows-workflow-foundation/media/outlineviewinworkflowdesigner.jpg "OutlineViewinWorkflowDesigner")  
  
### <a name="more-control-of-visibility-of-shell-bar-and-header-items"></a>Daha fazla denetim görünürlüğü Kabuk çubuğu ve üstbilgi öğeleri  
 Rehosted Tasarımcısı'nda bazı standart kullanıcı Arabirimi denetimlerini belirli bir iş akışı için anlamı olmayabilir ve kapalı olabilir. İçinde [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], bu özelleştirme yalnızca Tasarımcısı'nın altındaki Kabuk çubuğu tarafından desteklenir. İçinde [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], kabuk üstbilgi öğeleri Tasarımcı üstündeki görünürlüğünü ayarlayarak ayarlanabilir <xref:System.Activities.Presentation.View.DesignerView.WorkflowShellHeaderItemsVisibility%2A> uygun ile <xref:System.Activities.Presentation.View.ShellHeaderItemsVisibility> değeri.  
  
### <a name="auto-connect-and-auto-insert-in-flowchart-and-state-machine-workflows"></a>Otomatik olarak bağlanabilir ve akış çizelgesi ve durum makinesinin iş akışlarında otomatik ekleme  
 İçinde [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], akış iş akışında düğümler arasındaki bağlantıların el ile eklenmesi gerekiyordu. İçinde [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], akış ve Durum makinesi düğümünüz bir etkinlik araç kutusunu tasarımcı yüzeyine sürüklendiğinde görünür hale gelmiştir noktalarını otomatik olarak bağlanabilir. Bir etkinlik bu noktalarının birini otomatik olarak bırakarak gerekli bağlantı birlikte etkinlik ekler.  
  
 Aşağıdaki ekran görüntüsünde bir etkinlik Araç Kutusu'ndan sürüklendiğinde görünür hale gelmiştir ek noktalarını gösterir.  
  
 ![Otomatik bağlanma noktalarını gösteren akış çizelgesi başlangıç düğümü](../../../docs/framework/windows-workflow-foundation/media/autoconnect1.png "Autoconnect1")  
  
 Akış Çizelgesi düğümleri ve otomatik-iki düğüm arasında düğüm eklemek üzere durumları arasında etkinlikleri de bağlantıları sürüklenebilir. Aşağıdaki ekran görüntüsünde vurgulanan bağlanan satırı burada etkinlikler kullanılabilir Araç Kutusu'ndan sürüklenen ve bırakılan gösterir.  
  
 ![Otomatik&#45;etkinlikleri bırakarak için tanıtıcı Ekle](../../../docs/framework/windows-workflow-foundation/media/autoinsert.png "Autoinsert")  
  
 Otomatik olarak bağlanabilir ve otomatik ekleme rehosted Tasarımcısı'nda desteklenir.  
  
### <a name="designer-annotations"></a>Tasarımcı ek açıklamaları  
 Büyük iş akışları geliştirmeyi kolaylaştırmak için tasarımcı tasarım işlemini izlemenize yardımcı olmak için ekleme ek açıklamaları destekler. Ek açıklama etkinlikleri, durumları, akış çizelgesi düğümleri, değişkenler ve bağımsız değişkenler eklenebilir. Aşağıdaki ekran görüntüsünde Designer'a ek açıklamaları eklemek için kullanılan bağlam menüsünü gösterir.  
  
 ![Ek açıklama bağlam menüsü](../../../docs/framework/windows-workflow-foundation/media/annotationdialog.png "annotationdialog")  
  
 Tasarımcı ek açıklamaları rehosted Tasarımcısı'nda desteklenir.  
  
### <a name="define-and-consume-activitydelegate-objects-in-the-designer"></a>Tanımlama ve ActivityDelegate nesneleri Tasarımcısı'nda kullanma  
 Etkinlikler [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] kullanılan <xref:System.Activities.ActivityDelegate> burada iş akışını diğer bölümleri ile bir iş akışının yürütme destekliyordu, ancak bu yürütme noktaları genellikle kullanarak gerekli eşit miktarda kod yürütme noktalarını göstermek için nesneleri. Bu sürümde, geliştiricilerin tanımlayabilir ve iş akışı Tasarımcısı'nı kullanarak etkinlik temsilcileri kullanabilir. Daha fazla bilgi için bkz: [nasıl yapılır: tanımlama ve iş akışı Tasarımcısı'nda aktivite temsilcileri kullanma](/visualstudio/workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer).  
  
 Etkinlik temsilciler rehosted Tasarımcısı'nda desteklenir.  
  
### <a name="build-time-validation"></a>Derleme zamanı doğrulama  
 İçinde [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], iş akışı doğrulama hataları derleme hataları bir iş akışı projesinde derleme sırasında sayılan doğru. Bu, bir iş akışı derleme geliyordu bile iş akışı doğrulama hataları zamanki proje başarılı. İçinde [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], iş akışı doğrulama hatalara yapılandırmanın başarısız olmasına neden olabilir.  
  
> [!WARNING]
>  Derleme zamanı doğrulama rehosted Tasarımcısı'nda desteklenmiyor.  
  
### <a name="design-time-background-validation"></a>Tasarım zamanı arka plan doğrulama  
 İçinde [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], iş akışları kullanıcı arabirimini karmaşık ya da zaman alıcı doğrulama işlemi sırasında potansiyel olarak askıda kalabilir ön plan işlemi olarak doğrulandı. Böylece kullanıcı arabirimini engellenmez iş akışı doğrulama şimdi bir arka plan iş parçacığı üzerinde gerçekleşir.  
  
 Tasarım zamanı arka plan doğrulama rehosted Tasarımcısı'nda desteklenir.  
  
### <a name="view-state-located-in-a-separate-location-in-xaml-files"></a>XAML dosyaları ayrı bir konumda bulunan görünüm durumu  
 İçinde [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], Görünüm durumu bilgisini bir iş akışı için birçok farklı konumlarda XAML dosyası üzerinde depolanır. XAML doğrudan okuma ya da Görünüm durumu bilgileri kaldırmak için kod yazma isteyen geliştiriciler için kullanışsız budur. İçinde [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], Görünüm durumu bilgisini XAML dosyasındaki XAML dosyası içinde ayrı bir öğe olarak serileştirilmiş.  Kolayca geliştiriciler bulun ve bir etkinlik görünüm durumu bilgilerini düzenleyin veya Görünüm durumu tamamen kaldırın.  
  
 Bu özellik rehosted iş akışı Tasarımcısı'nda desteklenir.  
  
### <a name="opt-in-for-workflow-45-features-in-rehosted-designer"></a>İş akışı 4.5 özellikleri rehosted Tasarımcısı'nda kabulü  
 Geriye dönük uyumluluğu korumak için bazı yeni özellikler dahil [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] rehosted Tasarımcısı'nda varsayılan olarak etkin değildir. Bu rehosted Tasarımcısı'nı kullanan mevcut uygulamaları en son sürüme güncelleştirerek ayrılır değil olduğundan emin olmaktır. Rehosted Tasarımcısı'nda yeni özellikleri etkinleştirmek için ya da ayarlamak <xref:System.Activities.Presentation.DesignerConfigurationService.TargetFrameworkName%2A> için ".Net Framework 4.5", veya tek tek üyeleri <xref:System.Activities.Presentation.DesignerConfigurationService> tek tek özellikleri etkinleştirmek için.  
  
## <a name="new-workflow-development-models"></a>Yeni iş akışı geliştirme modelleri  
 Akış Çizelgesi ve sıralı iş akışı geliştirme modelleri ek olarak, bu sürüm durum makinesinin iş akışları ve sözleşme ilk iş akışı hizmetleri içerir.  
  
### <a name="state-machine-workflows"></a>Durum makinesi iş akışları  
 Durum makinesi iş akışları, .NET Framework 4.0.1 bir parçası olarak sunulmuştu [Microsoft .NET Framework 4 Platform Güncelleştirmesi 1](http://go.microsoft.com/fwlink/?LinkID=215092). Bu, birkaç yeni sınıflar ve Durum makinesi iş akışları oluşturmak geliştiriciler izin etkinlikler güncelleştirmenin. Bu sınıf ve etkinlikler için güncelleştirilmiş [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]. Güncelleştirmeler şunları içerir:  
  
1.  Kesme noktaları durumlarına ayarlama özelliği  
  
2.  Geçişler iş akışı Tasarımcısı'nda kopyalayıp olanağı  
  
3.  Paylaşılan tetikleyici geçiş oluşturma için tasarımcı desteği  
  
4.  Durum makinesinin iş akışları dahil olmak üzere, oluşturmak için kullanılan etkinliklerin: <xref:System.Activities.Statements.StateMachine>, <xref:System.Activities.Statements.State>, ve <xref:System.Activities.Statements.Transition>  
  
 Aşağıdaki ekran görüntüsünde tamamlanan durumu makine akışından gösterir [başlangıç Öğreticisi](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md) adım [nasıl yapılır: bir Durum makinesi iş akışı oluşturma](../../../docs/framework/windows-workflow-foundation/how-to-create-a-state-machine-workflow.md).  
  
 ![Durum makinesi iş akışı tamamlandı](../../../docs/framework/windows-workflow-foundation/media/wfstatemachinegettingstartedtutorialcomplete.JPG "WFStateMachineGettingStartedTutorialComplete")  
  
 Durum makinesi iş akışları oluşturma hakkında daha fazla bilgi için bkz: [durumu makine iş akışları](../../../docs/framework/windows-workflow-foundation/state-machine-workflows.md). Durum makinesi iş akışları rehosted Tasarımcısı'nda desteklenir.  
  
### <a name="contract-first-workflow-development"></a>Önce anlaşma iş akışı geliştirme  
 Önce anlaşma iş akışı geliştirme aracı, kod sözleşmede ilk tasarım sonra Visual Studio birkaç tıklama ile her işlemi temsil eden araç kutusu otomatik olarak bir etkinlik şablonu oluşturmak, geliştirici sağlar. Bu etkinlikler, ardından anlaşma tarafından tanımlanan işlemleri uygulayan bir iş akışı oluşturmak için kullanılır. İş Akışı Tasarımcısı'nı bu işlemler uygulanır ve iş akışının imza sözleşme imza eşleşen emin olmak için iş akışı hizmeti doğrular. Geliştirici, ayrıca bir iş akışı hizmeti uygulanan sözleşmeleri koleksiyonu ile ilişkilendirebilirsiniz. Önce anlaşma iş akışı hizmeti geliştirme hakkında daha fazla bilgi için bkz: [nasıl yapılır: varolan bir hizmet sözleşmesini tüketen bir iş akışı hizmeti oluşturma](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md).  
  
> [!WARNING]
>  Önce anlaşma iş akışı geliştirme iş akışı Tasarımcısı'nda desteklenmiyor.
