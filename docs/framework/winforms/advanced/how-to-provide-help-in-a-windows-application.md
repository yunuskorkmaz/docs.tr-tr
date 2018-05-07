---
title: 'Nasıl yapılır: Bir Windows Uygulamasında Yardım Sağlama'
ms.date: 03/30/2017
helpviewer_keywords:
- Help [Windows Forms], Windows applications
- HTML Help [Windows Forms], Windows Forms
- Windows applications [Windows Forms], providing Help
- HelpProvider component [Windows Forms]
- forms [Windows Forms], providing Help
ms.assetid: 7c4e5cec-2bd2-4f0b-8d75-c2b88929bd61
ms.openlocfilehash: 3df8f6eaee72ebdd6cbd03d0bdfde5a7d2270129
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-provide-help-in-a-windows-application"></a>Nasıl yapılır: Bir Windows Uygulamasında Yardım Sağlama
Kullanabileceğiniz <xref:System.Windows.Forms.HelpProvider> Windows Forms özel denetimlerinde Yardım dosyası içindeki Yardım konuları iliştirmek için bileşen. Yardım dosyası HTML veya HTMLHelp olabilir 1.x veya büyük biçimi.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-provide-help"></a>Yardım almak için  
  
1.  Gelen **araç**, sürükleyin bir <xref:System.Windows.Forms.HelpProvider> formunuza bileşen.  
  
     Bileşen Windows Form Tasarımcısı sonundaki tepsisinde yer alacaktır.  
  
2.  İçinde **özellikleri** penceresindeki ayarlayın <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> .chm, .col veya .htm Yardım dosyasına özelliği.  
  
3.  Başka bir denetim formunuzda vardır ve buna seçin **özellikleri** penceresindeki ayarlayın <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A> özelliği.  
  
     Bu geçtiğini dizedir <xref:System.Windows.Forms.HelpProvider> uygun Yardım konusunu Göndereceğim için Yardım dosyasına bileşen.  
  
4.  İçinde **özellikleri** penceresindeki ayarlayın <xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> değerini özelliğine <xref:System.Windows.Forms.HelpNavigator> numaralandırması.  
  
     Bu şekilde belirler **HelpKeyword** özelliği Yardım sistemine geçirilir. Aşağıdaki tabloda olası ayarlar ve açıklamaları gösterilmektedir.  
  
    |Üye Adı|Açıklama|  
    |-----------------|-----------------|  
    |AssociateIndex|Belirtilen bir konu için dizin belirtilen URL'de gerçekleştirildiğini belirtir.|  
    |Bul|Belirtilen URL'ın arama sayfası görüntüleneceğini belirtir.|  
    |Dizin|Belirtilen URL dizinini görüntüleneceğini belirtir.|  
    |KeywordIndex|Aranacak anahtar sözcüğü ve belirtilen URL'de gerçekleştirilecek eylemi belirtir.|  
    |TableOfContents|HTML 1.0 Yardım dosyasının içindekileri görüntüleneceğini belirtir.|  
    |Konu|Belirtilen URL tarafından başvurulan konu görüntüleneceğini belirtir.|  
  
 Çalışma zamanında F1 tuşuna basarak olduğunda denetim —, ayarladığınız için **HelpKeyword** ve **HelpNavigator** özellikleri — sahip odak ile ilgili Yardım dosyası açılır <xref:System.Windows.Forms.HelpProvider> bileşeni.  
  
 Şu anda **HelpNamespace** özelliği Yardım dosyaları üç aşağıdaki biçimlerde destekler: HTMLHelp 1.x, HTMLHelp 2.0 ve HTML. Bu nedenle, ayarlayabileceğiniz **HelpNamespace** bir Web sayfası gibi bir http:// adresi özelliğine. Bu yapıldığında, içinde belirtilen dize içeren Web sayfasına varsayılan tarayıcı açılır **HelpKeyword** bağlantı kullanılan özellik. Bağlantı, bir HTML sayfasında belirli bir kısmını atlamak için kullanılır.  
  
> [!IMPORTANT]
>  Uygulamanızda kullanmadan önce bir istemciden gönderilen herhangi bir bilgi denetlemek dikkatli olun. Kötü niyetli kullanıcılar veya yürütülebilir komut dosyası, SQL deyimlerini veya başka bir kod ekleme göndermeye. Bir kullanıcının giriş görüntülemek, bir veritabanında saklamak veya çalışma önce olmayabilecek bilgi içermiyor denetleyin. Bir normal şekilde anahtar sözcükler "Komut dosyası" gibi bir kullanıcıdan giriş aldığınızda aramak için normal bir ifade kullanmaktır.  
  
 Aynı zamanda <xref:System.Windows.Forms.HelpProvider> , onu Windows Forms denetimleri için Yardım dosyalarını görüntülemek için yapılandırılmış olsa bile açılır Yardım göstermek için bileşeni. Daha fazla bilgi için bkz: [nasıl yapılır: Görüntü açılır Yardım](../../../../docs/framework/winforms/advanced/how-to-display-pop-up-help.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: Açılır Yardımı Görüntüleme](../../../../docs/framework/winforms/advanced/how-to-display-pop-up-help.md)  
 [ToolTips Kullanarak Denetim Yardımı](../../../../docs/framework/winforms/advanced/control-help-using-tooltips.md)  
 [Windows Forms'ta Kullanıcı Yardımını Tümleştirme](../../../../docs/framework/winforms/advanced/integrating-user-help-in-windows-forms.md)  
 [Windows Forms](../../../../docs/framework/winforms/index.md)
