---
title: "İzlenecek yol: Dayama Çizgileri Kullanarak Windows Forms'ta Denetimleri Düzenleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [Windows Forms], arranging with snaplines
- snaplines [Windows Forms], arranging Windows Forms controls
- SnapLine class [Windows Forms], walkthroughs
- Windows Forms controls, arranging
ms.assetid: d5c9edc7-cf30-4a97-8ebe-201d569340f8
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: be514f435b787c770eca114d42bee5c1424a40c3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-arranging-controls-on-windows-forms-using-snaplines"></a>İzlenecek yol: Dayama Çizgileri Kullanarak Windows Forms'ta Denetimleri Düzenleme
Formunuza denetimler tam yerleşimi, pek çok uygulama yüksek önceliktir. Windows Form Tasarımcısı bunu gerçekleştirmek için birçok düzeni Araçlar verir. En önemlisi, biri <xref:System.Windows.Forms.Design.Behavior.SnapLine> özelliği.  
  
 Dayama çizgileri diğer denetimleri denetimleriyle hizalamak tam olarak nereye gösterir. Bunlar ayrıca, Windows kullanıcı arabirimi yönergelerine belirtildiği gibi denetimler arasındaki kenar boşlukları için önerilen uzaklıkları gösterir. Ayrıntılar için bkz [kullanıcı arabirimi tasarımı ve geliştirme](http://go.microsoft.com/FWLink/?LinkId=83878).  
  
 Dayama çizgileri kolaylaştırır denetimleriniz NET için hizalamak profesyonel görünüm ve davranış (Görünüm).  
  
 Bu örneklerde gösterilen görevler aşağıdakileri içerir:  
  
-   Windows Forms projesi oluşturma  
  
-   Aralık ve dayama çizgileri kullanarak denetimleri hizalama  
  
-   Form ve kapsayıcı kenar boşluklarını hizalama  
  
-   Gruplandırılmış denetimleri hizalama  
  
-   Dayama çizgileri boyutuna anahat oluşturma denetim yerleştirmek için kullanma  
  
-   Bir Denetim Araç Kutusu'ndan sürüklendiğinde dayama çizgileri kullanarak  
  
-   Dayama çizgileri kullanarak denetimleri yeniden boyutlandırma  
  
-   Bir etikete bir denetimin metni hizalama  
  
-   Dayama çizgileri ile klavye gezinti kullanma  
  
-   Dayama çizgileri ve Düzen panelleri  
  
-   Dayama çizgileri devre dışı bırakma  
  
 İşiniz bittiğinde dayama çizgileri özelliği tarafından yürütülen düzeni rol anlaşılması gerekir.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="creating-the-project"></a>Projeyi Oluşturma  
 Projeyi oluşturmak ve formu ayarlamak için ilk adımdır bakın.  
  
#### <a name="to-create-the-project"></a>Proje oluşturmak için  
  
1.  "SnaplineExample" adlı bir Windows tabanlı bir uygulama projesi oluşturun. Ayrıntılar için bkz [nasıl yapılır: bir Windows uygulaması projesi oluşturduğunuzda](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
2.  Formu Form tasarımcısında seçin.  
  
## <a name="spacing-and-aligning-controls-using-snaplines"></a>Aralık ve dayama çizgileri kullanarak denetimleri hizalama  
 Dayama çizgileri formunuza denetimler hizalamak için doğru ve sezgisel bir yol sağlar. Başka bir denetim veya denetimleri kümesini Hizala konumu yakınında seçilmiş bir denetim veya denetimlerin taşıdığınız zaman görünürler. "Diğer denetimleri taşırken seçiminiz için önerilen konum Daya".  
  
#### <a name="to-arrange-controls-using-snaplines"></a>Dayama çizgileri kullanarak denetimlerini düzenlemek için  
  
1.  Sürükleme bir <xref:System.Windows.Forms.Button> gelen denetim **araç** formunuza.  
  
2.  Taşıma <xref:System.Windows.Forms.Button> sağ alt köşedeki form denetimi. Not olarak görünür dayama çizgileri <xref:System.Windows.Forms.Button> alt ve sağ kenarlık form denetimi yaklaşıyor. Bu dayama çizgileri denetiminin Kenarlıklar ve form arasındaki önerilen uzaklığı görüntüler.  
  
3.  Taşıma <xref:System.Windows.Forms.Button> etrafında kenarlık dayama çizgileri göründüğü Not ve form denetimi. İşiniz bittiğinde, taşıma <xref:System.Windows.Forms.Button> formun Merkezi Denetim.  
  
4.  Başka bir sürükleyin <xref:System.Windows.Forms.Button> gelen denetim **araç** formunuza.  
  
5.  İkinci taşıma <xref:System.Windows.Forms.Button> ilk neredeyse düzeyi kadar denetim. Her iki düğmeleri metin taban çizgisini görünür snapline unutmayın ve taşıdığınız denetim düzeyi diğer denetimi ile tam olarak bir konuma tutturur not edin.  
  
6.  İkinci taşıma <xref:System.Windows.Forms.Button> doğrudan ilk konumlandırılmış kadar denetim. Her iki düğmeleri sol ve sağ kenarları boyunca görüntülenen ve denetimi, bir denetimi ile tam olarak hizalanır bir konuma taşıma yapışır olduğuna dikkat edin dayama çizgileri unutmayın.  
  
7.  Aşağıdakilerden birini seçin <xref:System.Windows.Forms.Button> denetler ve bunu diğer yakın, neredeyse dokunmak kadar. Bunlar arasında görünür snapline unutmayın. Bu uzaklık denetimleri Kenarlıklar arasındaki önerilen uzaklığı ' dir. Ayrıca, taşıdığınız denetim bu konuma tutturur unutmayın.  
  
8.  İki <xref:System.Windows.Forms.Panel> gelen denetimleri **araç** formunuza.  
  
9. Aşağıdakilerden birini taşıma <xref:System.Windows.Forms.Panel> ilk neredeyse düzeyi kadar denetler. Her iki denetimleri üst ve alt kenarları boyunca görüntülenen ve taşıdığınız denetim düzeyi diğer denetimi ile tam olarak bir konuma tutturur Not dayama çizgileri unutmayın.  
  
## <a name="aligning-to-form-and-container-margins"></a>Form ve kapsayıcı kenar boşluklarını hizalama  
 Dayama çizgileri form ve kapsayıcı kenar boşluklarına, denetimleri tutarlı bir şekilde hizalayın yardımcı olur.  
  
#### <a name="to-align-controls-to-form-and-container-margins"></a>Form ve kapsayıcı kenar boşluklarını denetimlere hizalamak için  
  
1.  Aşağıdakilerden birini seçin <xref:System.Windows.Forms.Button> denetler ve taşırsanız, formun sağ kenarlığın yakın bir snapline görünene kadar. Sağ kenarlığın snapline's mesafe denetimin toplamıdır <xref:System.Windows.Forms.Control.Margin%2A> özelliği ve formun <xref:System.Windows.Forms.Control.Padding%2A> özellik değerleri.  
  
> [!NOTE]
>  Formun <xref:System.Windows.Forms.Control.Padding%2A> özelliği için 0,0,0,0 ayarlanmışsa, Windows Form Tasarımcısı formu bir gölgeli verir <xref:System.Windows.Forms.Control.Padding%2A> 9,9,9,9 değeri. Bu davranışı geçersiz kılma 0,0,0,0 dışında bir değere atayın.  
  
1.  Değerini değiştirme <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Margin%2A> genişleterek özelliği <xref:System.Windows.Forms.Control.Margin%2A> girişi **özellikleri** penceresi ve ayarı <xref:System.Windows.Forms.Padding.All%2A> özelliğinin 0. Ayrıntılar için bkz [izlenecek yol: yerleştirmede çıkışı Windows Forms denetimleri doldurma, kenar boşlukları ve AutoSize özelliği ile](../../../../docs/framework/winforms/controls/windows-forms-controls-padding-autosize.md).  
  
2.  Taşıma <xref:System.Windows.Forms.Button> bir snapline görünene kadar bu formun sağ kenarlığın yakın denetim. Bu uzaklık şimdi formun değeriyle verilir <xref:System.Windows.Forms.Control.Padding%2A> özelliği.  
  
3.  Sürükleme bir <xref:System.Windows.Forms.GroupBox> gelen denetim **araç** formunuza.  
  
4.  Değerini değiştirmek <xref:System.Windows.Forms.GroupBox> denetimin <xref:System.Windows.Forms.Control.Padding%2A> genişleterek özelliği <xref:System.Windows.Forms.Control.Padding%2A> girişi **özellikleri** penceresi ve ayarı <xref:System.Windows.Forms.Padding.All%2A> 10 özelliği.  
  
5.  Sürükleme bir <xref:System.Windows.Forms.Button> gelen denetim **araç** içine <xref:System.Windows.Forms.GroupBox> denetim.  
  
6.  Taşıma <xref:System.Windows.Forms.Button> sağ kenarlığını yakın denetim <xref:System.Windows.Forms.GroupBox> bir snapline görünene kadar denetim. Taşıma <xref:System.Windows.Forms.Button> denetimine <xref:System.Windows.Forms.GroupBox> denetim ve dayama çizgileri göründüğü unutmayın.  
  
## <a name="aligning-to-grouped-controls"></a>Gruplandırılmış denetimleri hizalama  
 Dayama çizgileri gruplandırılmış denetimleri hizalama için kullanabileceğiniz de olarak denetimleri içinde bir <xref:System.Windows.Forms.GroupBox> denetim.  
  
#### <a name="to-align-to-grouped-controls"></a>Gruplanmış denetimlere hizalamak için  
  
1.  Denetimleri form üzerinde ikisinden seçin. Seçimi hareket ettirin ve seçiminizi ve diğer denetimlerin arasında görünür dayama çizgileri not edin.  
  
2.  Sürükleme bir <xref:System.Windows.Forms.GroupBox> gelen denetim **araç** formunuza.  
  
3.  Sürükleme bir <xref:System.Windows.Forms.Button> gelen denetim **araç** içine <xref:System.Windows.Forms.GroupBox> denetim.  
  
4.  Aşağıdakilerden birini seçin <xref:System.Windows.Forms.Button> denetler ve taşıyabilirsiniz <xref:System.Windows.Forms.GroupBox> denetim. Not kenarlarında görünür dayama çizgileri <xref:System.Windows.Forms.GroupBox> denetim. Ayrıca kenarlarında görünür dayama çizgileri unutmayın <xref:System.Windows.Forms.Button> tarafından bulunan denetim <xref:System.Windows.Forms.GroupBox> denetim. Bir kapsayıcı denetiminin alt denetimleri dayama çizgileri da destekler.  
  
## <a name="using-snaplines-to-place-a-control-by-outlining-its-size"></a>Dayama çizgileri boyutuna anahat oluşturma denetim yerleştirmek için kullanma  
 Dayama çizgileri Yardım, Hizala önce onları bir form üzerinde yerleştirdiğinizde denetler.  
  
#### <a name="to-use-snaplines-to-place-a-control-by-outlining-its-size"></a>Anahat oluşturma boyutuna göre bir denetim yerleştirmek için dayama çizgileri kullanmak için  
  
1.  İçinde **araç**, tıklatın <xref:System.Windows.Forms.Button> denetimi simgesi. Bu form üzerine sürükleyin değil.  
  
2.  Fare işaretçisini formun tasarım yüzeyi taşıyın. Bir artı kıl ile işaretçi Not <xref:System.Windows.Forms.Button> bağlı denetimi simgesi. Ayrıca hizalanmış konumlar için önermek için görünür dayama çizgileri unutmayın <xref:System.Windows.Forms.Button> denetim.  
  
3.  ' A tıklayın ve fare düğmesini basılı tutun.  
  
4.  Fare işaretçisini formun çevresinde sürükleyin. Anahat, konum ve boyut denetiminin belirten çizileceğini unutmayın.  
  
5.  Form üzerinde başka bir denetimi hizalar kadar işaretçiyi sürükleyin. Hizalama belirtmek için bir snapline göründüğüne dikkat edin.  
  
6.  Fare düğmesini bırakın. Denetim konumu ve boyutu anahat tarafından gösterilen konumunda oluşturulur.  
  
## <a name="using-snaplines-when-dragging-a-control-from-the-toolbox"></a>Bir Denetim Araç Kutusu'ndan sürüklendiğinde dayama çizgileri kullanarak  
 Dayama çizgileri Yardım, Hizala denetimleri onlardan sürüklediğinizde **araç** formunuza.  
  
#### <a name="to-use-snaplines-when-dragging-a-control-from-the-toolbox"></a>Dayama çizgileri Denetim Araç Kutusu'ndan sürüklendiğinde kullanmak için  
  
1.  Sürükleme bir <xref:System.Windows.Forms.Button> gelen denetim **araç** formunuza, ancak fare düğmesini bırakmaz.  
  
2.  Fare işaretçisini formun tasarım yüzeyi taşıyın. İşaretçinin konumunda belirtmek için değiştiğine dikkat edin yeni <xref:System.Windows.Forms.Button> denetiminin oluşturulabilir.  
  
3.  Fare işaretçisini formun çevresinde sürükleyin. İçin hizalanmış konumlarına önermek için görünür dayama çizgileri Not <xref:System.Windows.Forms.Button> denetim. Diğer denetimleriyle hizalanır bir konumunu bulur.  
  
4.  Fare düğmesini bırakın. Denetim dayama çizgileri tarafından belirtilen konumda oluşturulur.  
  
## <a name="resizing-controls-using-snaplines"></a>Dayama çizgileri kullanarak denetimleri yeniden boyutlandırma  
 Dayama çizgileri yardımcı bunları değiştirdikçe denetimleri hizalayın.  
  
#### <a name="to-resize-a-control-using-snaplines"></a>Dayama çizgileri kullanarak denetim yeniden boyutlandırmak için  
  
1.  Sürükleme bir <xref:System.Windows.Forms.Button> gelen denetim **araç** formunuza.  
  
2.  Yeniden boyutlandırma <xref:System.Windows.Forms.Button> denetimi boyutlandırma ve sürükleyerek köşe kapmasını biri tarafından. Ayrıntılar için bkz [nasıl yapılır: Windows formlarında denetimleri yeniden boyutlandırma](../../../../docs/framework/winforms/controls/how-to-resize-controls-on-windows-forms.md).  
  
3.  Aşağıdakilerden birini kadar boyutlandırma tutamacını sürükleyin <xref:System.Windows.Forms.Button> denetimin Kenarlıklar başka bir denetimle hizalanması. Bir snapline göründüğüne dikkat edin. Ayrıca, boyutlandırma tutamacını snapline tarafından belirtilen konuma tutturur unutmayın.  
  
4.  Yeniden boyutlandırma <xref:System.Windows.Forms.Button> farklı yönlerde denetlemek ve farklı denetimleri boyutlandırma tanıtıcısını Hizala. Dayama çizgileri hizalaması belirtmek için çeşitli yönleri nasıl göründüğünü unutmayın.  
  
## <a name="aligning-a-label-to-a-controls-text"></a>Bir etikete bir denetimin metni hizalama  
 Bazı denetimler için görüntülenen metin için diğer denetimleri hizalama snapline sunar.  
  
#### <a name="to-align-a-label-to-a-controls-text"></a>Denetimin metni etikete hizalamak için  
  
1.  Sürükleme bir <xref:System.Windows.Forms.TextBox> gelen denetim **araç** formunuza. Bıraktığınız zaman <xref:System.Windows.Forms.TextBox> forma denetim, akıllı etiket karakteri tıklatın ve seçin **textBox1 için metin ayarlamak** seçeneği. Ayrıntılar için bkz [izlenecek yol: gerçekleştirme ortak görevleri kullanarak akıllı etiketler Windows Forms denetimlerinde](../../../../docs/framework/winforms/controls/performing-common-tasks-using-smart-tags-on-wf-controls.md).  
  
2.  Sürükleme bir <xref:System.Windows.Forms.Label> gelen denetim **araç** formunuza.  
  
3.  Değerini değiştirme <xref:System.Windows.Forms.Label> denetimin <xref:System.Windows.Forms.Control.AutoSize%2A> özelliğine `true`. Denetimin kenarlık görüntü metnini uyacak şekilde ayarlanır unutmayın.  
  
4.  Taşıma <xref:System.Windows.Forms.Label> sol tarafındaki denetim <xref:System.Windows.Forms.TextBox> denetim altına ucuyla hizalanır şekilde <xref:System.Windows.Forms.TextBox> denetim. İki denetim alt kenarları boyunca görünen snapline unutmayın.  
  
5.  Taşıma <xref:System.Windows.Forms.Label> denetim kadar biraz yukarı <xref:System.Windows.Forms.Label> metin ve <xref:System.Windows.Forms.TextBox> metin hizalanır. Her iki denetim metin alanlarının zaman hizalanır görüntülenerek farklı stilde snapline unutmayın.  
  
## <a name="using-snaplines-with-keyboard-navigation"></a>Dayama çizgileri ile klavye gezinti kullanma  
 Dayama çizgileri Yardım, Hizala zaman, bunları klavyenin ok tuşlarını kullanarak düzenleme denetler.  
  
#### <a name="to-use-snaplines-with-keyboard-navigation"></a>Dayama çizgileri ile klavye gezinti kullanmak için  
  
1.  Sürükleme bir <xref:System.Windows.Forms.Button> gelen denetim **araç** formunuza. Formun sol üst köşesindeki yerleştirin.  
  
2.  CTRL + AŞAĞI OK tuşlarına basın. Denetimi ilk kullanılabilir yatay hizalama konumu formunu aşağı taşır unutmayın.  
  
3.  Formun alt kısmındaki denetim ulaşana kadar CTRL + AŞAĞI OK tuşlarına basın. Formun hareket ederken kapladığı konumlar unutmayın.  
  
4.  CTRL + sağ ok tuşlarına basın. Denetim form üzerinde ilk kullanılabilir dikey hizalama konuma taşınır unutmayın.  
  
5.  Denetim formun tarafı ulaşana kadar CTRL + sağ ok tuşlarına basın. Form üzerinde hareket ederken kapladığı konumlar unutmayın.  
  
6.  Formun çevresinde denetimi ok tuşları birlikte taşıyın. Denetimin kapladığı konumlar ve bunları eşlik dayama çizgileri unutmayın.  
  
7.  SHIFT + herhangi bir ok tuşu yeniden boyutlandırmak için tuşlarına basın <xref:System.Windows.Forms.Button> denetimi tarafından bir piksel artırır.  
  
8.  Yeniden boyutlandırmak için CTRL + SHIFT + herhangi bir ok tuşuna basın <xref:System.Windows.Forms.Button> snapline artışlarla denetim.  
  
## <a name="snaplines-and-layout-panels"></a>Dayama çizgileri ve Düzen panelleri  
 Dayama çizgileri Düzen panelleri içinde devre dışı bırakılır.  
  
#### <a name="to-selectively-disable-snaplines"></a>Seçmeli olarak dayama çizgileri devre dışı bırakmak için  
  
1.  Sürükleme bir <xref:System.Windows.Forms.TableLayoutPanel> gelen denetim **araç** formunuza.  
  
2.  Çift <xref:System.Windows.Forms.Button> denetim simgesinde **araç**. Yeni bir düğme denetimi görünür Not <xref:System.Windows.Forms.TableLayoutPanel> denetimin ilk hücre.  
  
3.  Çift <xref:System.Windows.Forms.Button> denetim simgesinde **araç** iki kez daha fazla. Bu, boş bir hücreye bırakır <xref:System.Windows.Forms.TableLayoutPanel> denetim.  
  
4.  Sürükleme bir <xref:System.Windows.Forms.Button> gelen denetim **araç** boş hücresine <xref:System.Windows.Forms.TableLayoutPanel> denetim. Hiçbir dayama çizgileri görünür unutmayın.  
  
5.  Sürükleme <xref:System.Windows.Forms.Button> dışı denetim <xref:System.Windows.Forms.TableLayoutPanel> denetlemek ve taşıyabilirsiniz <xref:System.Windows.Forms.TableLayoutPanel> denetim. Dayama çizgileri yeniden göründüğüne dikkat edin.  
  
## <a name="disabling-snaplines"></a>Dayama çizgileri devre dışı bırakma  
 Dayama çizgileri varsayılan olarak açıktır. Dayama çizgileri seçmeli olarak devre dışı bırakabilir ya da, bunları tasarım ortamında devre dışı bırakabilirsiniz.  
  
#### <a name="to-selectively-disable-snaplines"></a>Seçmeli olarak dayama çizgileri devre dışı bırakmak için  
  
-   ALT tuşuna basın ve form geçici bir denetim taşıma while.  
  
     Hiçbir dayama çizgileri görünür ve denetim tüm olası hizalama konumlara Daya değil unutmayın.  
  
#### <a name="to-disable-snaplines-in-the-design-environment"></a>Dayama çizgileri tasarım ortamında devre dışı bırakmak için  
  
1.  Gelen **Araçları** menüsünde, açık **seçenekleri** iletişim kutusu. Windows Forms Tasarımcısı iletişim kutusunu açın. Ayrıntılar için bkz [genel, Windows Form Tasarımcısı, Seçenekler iletişim kutusu](http://msdn.microsoft.com/en-us/8dd170af-72f0-4212-b04b-034ceee92834).  
  
2.  Seçin **genel** düğümü. İçinde **Düzen modunu** bölümünde, seçimden değiştirme **dayama çizgileri** için **Snaptogrıd**.  
  
3.  Ayarı uygulamak için Tamam'ı tıklatın.  
  
4.  Formdaki bir denetime seçin ve diğer denetimlerin taşıyın. Dayama çizgileri görünmez unutmayın.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Dayama çizgileri, form üzerinde denetimleri hizalama, sezgisel bir yol sunar. Daha fazla araştırması için öneriler şunlardır:  
  
-   İç içe geçirmeyi deneyin bir <xref:System.Windows.Forms.GroupBox> başka denetimine <xref:System.Windows.Forms.GroupBox> denetim. Yerine bir <xref:System.Windows.Forms.Button> alt denetimine <xref:System.Windows.Forms.GroupBox> denetimi ve üst içinde başka bir <xref:System.Windows.Forms.GroupBox> denetim. Taşıma <xref:System.Windows.Forms.Button> etrafında nasıl dayama çizgileri kapsayıcı sınırları arası görmek için kontrol eder.  
  
-   Bir sütun oluşturmak <xref:System.Windows.Forms.TextBox> denetimleri ve karşılık gelen bir sütuna, <xref:System.Windows.Forms.Label> kontrol eder. Değerini <xref:System.Windows.Forms.Label> denetimleri <xref:System.Windows.Forms.Control.AutoSize%2A> özelliğine `true`. Dayama çizgileri gidebilir <xref:System.Windows.Forms.Label> kendi görüntülenen metni metin ile hizalanır şekilde denetimleri <xref:System.Windows.Forms.TextBox> denetimleri.  
  
 Windows kullanıcı arabirimi tasarımı hakkında daha fazla bilgi için bkz: kitap *Microsoft Windows kullanıcı deneyimi, kullanıcı arabirimi geliştiricilerin ve tasarımcıların resmi yönergeleri* Redmond, WA: Microsoft Press, 1999. (USBN: 0-7356-0566-1).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.Design.Behavior.SnapLine>  
 [İzlenecek yol: FlowLayoutPanel kullanarak Windows Forms'ta denetimleri düzenleme](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  
 [İzlenecek yol: Bir TableLayoutPanel kullanarak Windows Forms'ta denetimleri düzenleme](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
 [İzlenecek yol: Windows Forms denetimleri doldurma, kenar boşlukları ve AutoSize özelliği ile düzenleme](../../../../docs/framework/winforms/controls/windows-forms-controls-padding-autosize.md)  
 [Windows Forms'ta denetimleri düzenleme](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)
