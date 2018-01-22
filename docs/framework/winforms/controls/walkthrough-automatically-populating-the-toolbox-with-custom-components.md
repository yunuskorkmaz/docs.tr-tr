---
title: "İzlenecek yol: Araç Kutusunu Otomatik Olarak Özel Bileşenlerle Doldurma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IToolboxService interface
- Toolbox [Windows Forms], populating
- custom components [Windows Forms], adding to Toolbox
ms.assetid: 2fa1e3e8-6b9f-42b2-97c0-2be57444dba4
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6b60d4ee7908a5ed9dcb3393132ba7d0bd0a6cb5
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-automatically-populating-the-toolbox-with-custom-components"></a>İzlenecek yol: Araç Kutusunu Otomatik Olarak Özel Bileşenlerle Doldurma
Bileşenlerinizi açık çözümdeki bir proje ile tanımlanır, bunlar otomatik olarak görünür **araç**, hiçbir eylem yapmanız gerekmez. El ile de doldurabilirsiniz **araç** kullanarak, özel bileşenlerle [seçin araç kutusu öğelerini iletişim kutusu (Visual Studio)](http://msdn.microsoft.com/library/bd07835f-18a8-433e-bccc-7141f65263bb), ancak **araç** hesap alır çözümünüzün öğelerinin aşağıdaki özelliklere sahip çıkışları oluşturun:  
  
-   Implements <xref:System.ComponentModel.IComponent>;  
  
-   Sahip olmayan <xref:System.ComponentModel.ToolboxItemAttribute> kümesine `false`;  
  
-   Sahip olmayan <xref:System.ComponentModel.DesignTimeVisibleAttribute> kümesine `false`.  
  
> [!NOTE]
>  **Araç** çözümünüzü projede tarafından oluşturulmuş olmayan öğeler görüntülenmez şekilde başvuru zincirleri izlemez.  
  
 Bu yönergeler, nasıl özel bir bileşen otomatik olarak görünür gösterir **araç** bileşen oluşturulduktan sonra. Bu örneklerde gösterilen görevler aşağıdakileri içerir:  
  
-   Windows Forms projesi oluşturma.  
  
-   Özel bir bileşen oluşturuluyor.  
  
-   Özel bir bileşen örneği oluşturma.  
  
-   Yüklemeyi kaldırma ve özel bir bileşen yeniden yükleniyor.  
  
 İşiniz bittiğinde, görürsünüz **araç** oluşturduğunuz bir bileşen ile doldurulur.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="creating-the-project"></a>Projeyi Oluşturma  
 İlk adım, projeyi oluşturmak ve formu ayarlamak için ' dir.  
  
#### <a name="to-create-the-project"></a>Proje oluşturmak için  
  
1.  Adlı bir Windows tabanlı bir uygulama projesi oluşturun `ToolboxExample`.  
  
     Daha fazla bilgi için bkz: [nasıl yapılır: bir Windows uygulaması projesi oluşturduğunuzda](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
2.  Yeni bir bileşen projeye ekleyin. Bu çağrı `DemoComponent`.  
  
     Daha fazla bilgi için bkz: [NIB: nasıl yapılır: Yeni proje öğeleri Ekle](http://msdn.microsoft.com/library/63d3e16b-de6e-4bb5-a0e3-ecec762201ce).  
  
3.  Projeyi oluşturun.  
  
4.  Gelen **Araçları** menüsünde tıklatın **seçenekleri** öğesi. Tıklatın **genel** altında **Windows Form Tasarımcısı** öğesi ve emin **AutoToolboxPopulate** seçeneği **True**.  
  
## <a name="creating-an-instance-of-a-custom-component"></a>Özel bir bileşen örneği oluşturma  
 Sonraki adım, formdaki özel bileşen örneği oluşturmaktır. Çünkü **araç** otomatik olarak yeni bileşen hesaplarını, bunun herhangi bir bileşen veya denetim oluşturma olarak kadar kolaydır.  
  
#### <a name="to-create-an-instance-of-a-custom-component"></a>Özel bir bileşen örneği oluşturmak için  
  
1.  Projenin formunda açmak **Forms Tasarımcısı**.  
  
2.  İçinde **araç**, olarak adlandırılan yeni sekmesini **ToolboxExample bileşenleri**.  
  
     Sekmesine tıkladığınızda göreceğiniz **DemoComponent**.  
  
    > [!NOTE]
    >  Performans nedenleriyle bileşenleri otomatik olarak doldurulmuş alanı **araç** özel bit eşlemler, görüntüleme ve <xref:System.Drawing.ToolboxBitmapAttribute> desteklenmiyor. Özel bir bileşen için bir simge görüntülemek için **araç**, kullanın **araç kutusu öğelerini Seç** , bileşeni yüklemek için iletişim kutusu.  
  
3.  Bileşeniniz formunuza sürükleyin.  
  
     Bileşen örneği oluşturulur ve eklenen **bileşen**.  
  
## <a name="unloading-and-reloading-a-custom-component"></a>Yüklemeyi kaldırma ve özel bir bileşen yeniden yükleniyor  
 **Araç** alır hesap her bileşenlerinin yüklü proje ve proje kaldırıldığında, projenin bileşenleri başvuruları kaldırır.  
  
#### <a name="to-experiment-with-the-effect-on-the-toolbox-of-unloading-and-reloading-components"></a>Yüklemeyi kaldırma ve bileşenleri yeniden yükleme araç etkisi deneme  
  
1.  Çözüm projeden kaldırın.  
  
     Yüklemeyi kaldırma projeler hakkında daha fazla bilgi için bkz: [NIB: nasıl yapılır: Unload ve yeniden projeleri](http://msdn.microsoft.com/library/abc0155b-8fcb-4ffc-95b6-698518a7100b). Kaydetmek için istenirse, seçin **Evet**.  
  
2.  Yeni bir ekleme **Windows uygulaması** çözüme proje. Formunda açmak **Tasarımcısı**.  
  
     **ToolboxExample bileşenleri** önceki Proje sekmesinden olduğu artık kaldırılmıştır.  
  
3.  Yeniden yükleme `ToolboxExample` projesi.  
  
     **ToolboxExample bileşenleri** sekmesinde şimdi görüntülenir.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Bu anlatımda gösterilir **araç kutusu** hesap bir projenin bileşenlerinin alır ancak **araç** ayrıca alır denetimleri hesabıdır. Ekleyerek ve denetim projeleri çözümünüzden kaldırılması, kendi özel denetimler ile deneyin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Genel, Windows Form Tasarımcısı, Seçenekler iletişim kutusu](http://msdn.microsoft.com/library/8dd170af-72f0-4212-b04b-034ceee92834)  
 [Nasıl yapılır: araç kutusu sekmeleri işlemek](http://msdn.microsoft.com/library/21285050-cadd-455a-b1f5-a2289a89c4db)  
 [Araç kutusu öğelerini Seç iletişim kutusu (Visual Studio)](http://msdn.microsoft.com/library/bd07835f-18a8-433e-bccc-7141f65263bb)  
 [Windows Forms’a Denetimler Yerleştirme](../../../../docs/framework/winforms/controls/putting-controls-on-windows-forms.md)
