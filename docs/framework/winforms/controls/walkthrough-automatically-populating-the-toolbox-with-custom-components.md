---
title: 'İzlenecek yol: Araç Kutusunu Otomatik Olarak Özel Bileşenlerle Doldurma'
ms.date: 03/30/2017
helpviewer_keywords:
- IToolboxService interface
- Toolbox [Windows Forms], populating
- custom components [Windows Forms], adding to Toolbox
ms.assetid: 2fa1e3e8-6b9f-42b2-97c0-2be57444dba4
ms.openlocfilehash: 6ecf69350b8337dc6049b73251809192b47dc2fb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61759914"
---
# <a name="walkthrough-automatically-populating-the-toolbox-with-custom-components"></a>İzlenecek yol: Araç Kutusunu Otomatik Olarak Özel Bileşenlerle Doldurma
Bileşenlerinizi açık çözümde bir proje tarafından tanımlanan, bunlar otomatik olarak görünür **araç kutusu**, sizin tarafınızdan gerekli herhangi bir işlem ile. El ile de doldurabilirsiniz **araç kutusu** kullanarak kendi özel bileşenlerle [seçin araç kutusu öğeleri iletişim kutusu (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/dyca0t6t(v=vs.100)), ancak **araç kutusu** alır çözümünüzün içindeki öğelerin aşağıdaki özelliklere sahip çıkışları derleme:  
  
- Implements <xref:System.ComponentModel.IComponent>;  
  
- Olmayan <xref:System.ComponentModel.ToolboxItemAttribute> kümesine `false`;  
  
- Olmayan <xref:System.ComponentModel.DesignTimeVisibleAttribute> kümesine `false`.  
  
> [!NOTE]
>  **Araç kutusu** , çözümde bir proje tarafından oluşturulmamış öğeleri görüntülenmez için başvuru zincirleri izlemez.  
  
 Bu izlenecek yol, nasıl özel bir bileşeni otomatik olarak görünür gösterir **araç kutusu** bileşeni derlendikten sonra. Bu kılavuzda gösterilen görevler aşağıdakileri içerir:  
  
- Bir Windows Forms projesi oluşturma.  
  
- Bir özel bileşene oluşturuluyor.  
  
- Özel bir bileşeninin örneği oluşturuluyor.  
  
- Kaldırma ve bir özel bileşene yeniden yükleniyor.  
  
 İşlemi tamamladığınızda, göreceksiniz **araç kutusu** oluşturmuş olduğunuz bir bileşeni ile doldurulur.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
## <a name="creating-the-project"></a>Projeyi Oluşturma  
 İlk adım projeyi oluşturmak ve formu ayarlamak için ' dir.  
  
#### <a name="to-create-the-project"></a>Proje oluşturmak için  
  
1. Adlı bir Windows tabanlı uygulama projesi oluşturma `ToolboxExample` (**dosya** > **yeni** > **proje**  >  **Visual C#** veya **Visual Basic** > **Klasik Masaüstü** > **Windows Forms uygulamalarındaki**).  
  
2. Yeni bir bileşen projeye ekleyin. Bu çağrı `DemoComponent`.  
  
     Daha fazla bilgi için [nasıl yapılır: Yeni proje öğeleri ekleme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w0572c5b(v=vs.100)).  
  
3. Projeyi oluşturun.  
  
4. Gelen **Araçları** menüsünde tıklatın **seçenekleri** öğesi. Tıklayın **genel** altında **Windows Form Tasarımcısı** emin olun ve öğe **AutoToolboxPopulate** seçeneği **True**.  
  
## <a name="creating-an-instance-of-a-custom-component"></a>Özel bileşen örneği oluşturma  
 Sonraki adım, formda özel bileşen örneği oluşturmaktır. Çünkü **araç kutusu** otomatik olarak hesapları yeni bileşeni için bu olarak herhangi bir bileşeni veya denetimi oluşturmak oldukça kolaydır.  
  
#### <a name="to-create-an-instance-of-a-custom-component"></a>Bir özel bileşene bir örneğini oluşturmak için  
  
1. Projenin formda açın **Form Tasarımcısı**.  
  
2. İçinde **araç kutusu**, adlı yeni sekmesini **ToolboxExample bileşenleri**.  
  
     Sekmesine tıklayın, sonra göreceğiniz **DemoComponent**.  
  
    > [!NOTE]
    >  Performans nedenleriyle bileşenleri otomatik olarak doldurulan alanında **araç kutusu** özel bit eşlemler, görüntüleme ve <xref:System.Drawing.ToolboxBitmapAttribute> desteklenmiyor. Özel bir bileşeni için bir simge görüntülemek için **araç kutusu**, kullanın **araç kutusu öğelerini Seç** iletişim kutusu, bileşeni yüklenemiyor.  
  
3. Bileşeniniz formunuza sürükleyin.  
  
     Bileşen örneği oluşturulur ve eklenen **bileşeni Tepsi**.  
  
## <a name="unloading-and-reloading-a-custom-component"></a>Bir özel bileşene yeniden yükleme ve kaldırma  
 **Araç kutusu** alır hesabı bileşenlerin her proje yüklendi ve bir proje kaldırıldığında, projenin bileşenleri başvurular kaldırır.  
  
#### <a name="to-experiment-with-the-effect-on-the-toolbox-of-unloading-and-reloading-components"></a>Bileşenleri yeniden yükleme ve kaldırma araç kutusu üzerindeki etkisini denemek için  
  
1. Çözümden proje Kaldır.  
  
     Projeleri kaldırma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Projeleri yeniden yükleyin ve kaldırma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/tt479x1t(v=vs.100)). Kaydetmeniz istenirse seçin **Evet**.  
  
2. Yeni bir **Windows uygulama** çözüme bir proje. Formda açın **Tasarımcısı**.  
  
     **ToolboxExample bileşenleri** , artık önceki projeyi sekmesinden kaybolur.  
  
3. Reload `ToolboxExample` proje.  
  
     **ToolboxExample bileşenleri** sekmesinde artık yeniden görüntülenir.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Bu izlenecek yol gösteren **araç kutusu** projenin bileşenlerinin alır ancak **araç kutusu** ayrıca alır denetimleri hesabıdır. İle kendi özel denetimler ekleyerek ve çözümünüze ait denetim projeleri kaldırma denemeler yapın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Genel, Windows Form Tasarımcısı, Seçenekler iletişim kutusu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/5aazxs78(v=vs.100))
- [Nasıl yapılır: Araç kutusu sekmeleri düzenleme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/66kwe227(v=vs.100))
- [Araç kutusu öğelerini Seç iletişim kutusu (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/dyca0t6t(v=vs.100))
- [Windows Forms’a Denetimler Yerleştirme](putting-controls-on-windows-forms.md)
