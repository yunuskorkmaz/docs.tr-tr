---
title: "Nasıl yapılır: Devralma Seçici İletişim Kutusunu Kullanarak Form Devralma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- inheritance [Windows Forms], forms
- Inheritance Picker dialog box
- inherited forms [Windows Forms], creating
ms.assetid: 969b4c04-12aa-4297-93a2-0ae747447823
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b330e84c14fa528fb84489e8fec16544144cf731
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-inherit-forms-using-the-inheritance-picker-dialog-box"></a>Nasıl yapılır: Devralma Seçici İletişim Kutusunu Kullanarak Form Devralma
Bir form veya başka bir nesneye devralmak için en kolay yolu kullanmaktır **devralma Seçici** iletişim kutusu. Bununla, diğer çözümleri önceden oluşturduğunuz kod veya kullanıcı arabirimi (UI) avantajlarından yararlanabilirler.  
  
> [!NOTE]
>  Bir formla devralınmalıdır için **devralma Seçici** iletişim kutusunda, bu formu içeren projeyi gerekir yerleşik bir yürütülebilir dosya veya DLL'e. Projeyi oluşturmak için tercih **yapı çözümü** gelen **yapı** menüsü.  
>   
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-create-a-windows-form-inherited-from-an-existing-form-by-using-the-inheritance-picker"></a>Varolan bir formdan devralma Seçici kullanarak devralınan bir Windows Form oluşturmak için  
  
1.  Gelen **proje** menüsünde seçin **Add Windows Form**.  
  
     **Yeni Öğe Ekle** iletişim kutusu açılır.  
  
2.  Seçin **devralınan Form** şablonu ve içinde ad **adı** kutusu. Tıklatın **Ekle** devam etmek için düğmesini.  
  
     **Devralma Seçici** iletişim kutusu açılır. Geçerli projenin forms içeriyorsa, bunlar görüntülenir **devralma Seçici** iletişim kutusu.  
  
3.  Bir formdan başka bir derlemede devralmak için tıklatın **Gözat** düğmesi.  
  
4.  İçinde **devralmak için bir bileşen içeren bir dosya seçin** iletişim kutusunda, istediğiniz modülü ve formu içeren projesine gidin.  
  
5.  Bunu seçin ve .exe veya .dll dosyasının adını tıklatın **açık** düğmesi.  
  
     Bu, olanak verir **devralma Seçici** iletişim kutusu, burada bileşen şimdi listelenir, onu bulunduğu proje yanı sıra.  
  
6.  Bileşeni seçin.  
  
     İçinde **Çözüm Gezgini**, bileşen projenize eklenir. Bir kullanıcı Arabirimi varsa, devralınan formun parçası olan denetimleri bir simge ile işaretlenir (![VisualBasicInheritanceSymbol ekran görüntüsü](../../../../docs/framework/winforms/advanced/media/vbinheritanceglyph.gif "vbInheritanceGlyph")), ve seçili olduğunda, belirten bir sınır vardır superclassed form üzerinde denetimi olan güvenlik düzeyi. Aşağıdaki tabloda farklı güvenlik düzeylerine karşılık davranışlar listelenmektedir.  
  
    |Güvenlik düzeyi denetimi|Kullanılabilir etkileşiminin Tasarımcısı ve Form devralınan ile Kod Düzenleyicisi|  
    |-------------------------------|--------------------------------------------------------------------------------|  
    |Ortak|Boyutlandırma ile standart kenarlık: denetim boyutlandırılmış ve taşındı. Denetim dahili olarak bunu bildiren sınıfı ve dışarıdan diğer sınıflar tarafından erişilebilir.|  
    |Korumalı|Boyutlandırma ile standart kenarlık: denetim boyutlandırılmış ve taşındı. Dahili olarak bunu bildirir sınıfı ve üst sınıfından devralan, ancak dış sınıfları tarafından erişilemez durumda herhangi bir sınıf tarafından erişilebilir.|  
    |Korumalı iç (korumalı Friend Visual Basic)|Boyutlandırma ile standart kenarlık: denetim boyutlandırılmış ve taşındı. Dahili olarak bunu bildirir sınıfı, üst sınıfından devralan herhangi bir sınıf ve onu içeren derlemenin diğer üyeleri tarafından erişilebilir.|  
    |Dahili (Visual Basic'te arkadaş)|Formdaki özellikleri görünür gösterilen hiçbir boyutlandırma, standart kenarlık **özellikleri** penceresi. Ancak, tüm yönlerini denetimi salt okunur olarak kabul edilir. Taşıyamaz veya denetim boyut veya özelliklerini değiştirin. Denetim bir grup kutusu gibi diğer denetimlerin bir kapsayıcı ise yeni denetimler eklenemez ve bu denetimleri ortak dahi mevcut denetimleri kaldırılamaz. Denetimi yalnızca onu içeren derlemenin diğer üyeleri tarafından erişilebilir.|  
    |Özel|Formdaki özellikleri görünür gösterilen hiçbir boyutlandırma, standart kenarlık **özellikleri** penceresi. Ancak, tüm yönlerini denetimi salt okunur olarak kabul edilir. Taşıyamaz veya denetim boyut veya özelliklerini değiştirin. Denetim bir grup kutusu gibi diğer denetimlerin bir kapsayıcı ise yeni denetimler eklenemez ve bu denetimleri ortak dahi mevcut denetimleri kaldırılamaz. Denetimi yalnızca onu tanımlandığı sınıfı tarafından erişilebilir.|  
  
     Taban formun görünüşünü değiştirme hakkında daha fazla bilgi için bkz: [taban formun görünüşünü değiştirmenin etkileri](../../../../docs/framework/winforms/advanced/effects-of-modifying-base-form-appearance.md).  
  
    > [!NOTE]
    >  Standart denetimler ve Windows Forms bileşenleri ile devralınan denetimleri ve bileşenleri birleştirdiğinizde z-sıralamasını çakışıyor karşılaşabilirsiniz. Z-sırasını tıklayarak yapılır değiştirerek bunu düzeltebilirsiniz **biçimi** işaret menüsünde **sipariş**ve ardından **öne** veya  **Geri Gönder**. Denetimleri z düzenini hakkında daha fazla bilgi için bkz: [nasıl yapılır: Windows Forms katman nesnelerde](../../../../docs/framework/winforms/controls/how-to-layer-objects-on-windows-forms.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Inherits Deyimi](~/docs/visual-basic/language-reference/statements/inherits-statement.md)  
 [using](~/docs/csharp/language-reference/keywords/using.md)  
 [Taban Formun Görünüşünü Değiştirmenin Etkileri](../../../../docs/framework/winforms/advanced/effects-of-modifying-base-form-appearance.md)  
 [Windows Forms Görsel Devralma](../../../../docs/framework/winforms/advanced/windows-forms-visual-inheritance.md)
