---
title: Denetim Türü Önerileri
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- user controls [Windows Forms], when to use
- custom controls [Windows Forms], types
- controls [Windows Forms], creating
ms.assetid: 5235fe9d-c36a-4c08-ae76-6cb90b50085e
ms.openlocfilehash: b2193c862b0bfe0ffbdc55f5d7073409b03a040d
ms.sourcegitcommit: acd8ed14fe94e9d4e3a7fb685fe83d05e941073c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/20/2019
ms.locfileid: "56442951"
---
# <a name="control-type-recommendations"></a>Denetim Türü Önerileri
Geliştirin ve yeni denetimler uygulamak için güç .NET Framework sağlar. Alışık olduğunuz kullanıcı denetimine ek olarak, artık kendi boyama gerçekleştirmek ve devralma yoluyla mevcut denetimleri genişletmek bile mümkün olmayan özel denetimler yazabiliyor de bulabilirsiniz. Denetimi oluşturmak için hangi tür zorlanabilirsiniz. Bu bölümde içinden denetimlerin çeşitli türler arasında devralma işlemi yapabileceğini ve projeniz için seçmek için türü ile ilgili dikkat edilmesi gerekenler verir farklar vurgulanmaktadır.  
  
> [!NOTE]
>  Web formlarında kullanmak üzere bir denetim yazmak istiyorsanız [özel ASP.NET sunucu denetimleri geliştirme](https://docs.microsoft.com/previous-versions/aspnet/zt27tfhy(v=vs.100)).  
  
## <a name="inheriting-from-a-windows-forms-control"></a>Devralmayı bir Windows Forms denetimi  
 Devralınan bir denetimi varolan herhangi bir Windows Forms denetimden türetebilirsiniz. Bu yaklaşım, tüm Windows Forms denetiminin devralınan işlevselliğini korumak ve ardından özel özellikler, yöntemler veya diğer işlevleri ekleyerek işlevselliği genişletmek için sağlar. Örneğin, türetilmiş bir denetim oluşturabilirsiniz <xref:System.Windows.Forms.TextBox> yalnızca sayı kabul edebilir ve bir değere dönüştürür giriş otomatik olarak. Bu tür bir denetim metin kutusundaki metin değiştirdiyseniz ve ek bir özellik sahip olduğunda çağrılan bir doğrulama kodu içerebilir değeri. Bazı denetimler de özel görünüşünü denetiminizin grafik arabirimine geçersiz kılarak ekleyebilirsiniz <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi temel sınıf.  
  
 Bir Windows Forms denetimi devralır:  
  
-   İhtiyacınız olan işlevleri çoğunu zaten varolan bir Windows Forms denetimi aynı.  
  
-   Yeni bir grafik ön uç için varolan bir denetimi tasarım istediğiniz veya özel bir grafik arabirim gerekmez.  
  
## <a name="inheriting-from-the-usercontrol-class"></a>UserControl sınıfından devralma  
 Bir kullanıcı denetimi, Windows Forms denetimleri ortak bir kapsayıcıya kapsüllenmiş koleksiyonudur. Kapsayıcı tüm her Windows Forms denetimleri ilişkilendirilmiş devralınan işlevselliğini içerir ve seçmeli olarak kullanıma sunmak ve bunların özelliklerini bağlama olanak tanır. Bir kullanıcı denetimi örneği veritabanından müşteri adresi verilerini görüntülemek üzere tasarlanmış bir denetimi olabilir. Bu denetim, her alanı ve düğme denetimleri Kayıtlarda gezinmek için görüntülenecek birkaç metin kutuları verilebilir. Veri bağlama özellikleri seçmeli olarak sunulabilir ve tüm denetim paketlenmeli ve uygulamadan uygulamaya yeniden kullanılabilir.  
  
 Devralınan <xref:System.Windows.Forms.UserControl> , sınıf:  
  
-   Çeşitli Windows Forms denetimleri işlevlerini tek bir yeniden kullanılabilir biriminde birleştirmek istediğiniz.  
  
## <a name="inheriting-from-the-control-class"></a>Denetim sınıfından devralma  
 Sıfırdan büyük ölçüde devralarak oluşturmak için bir denetim oluşturmak için başka bir yolu olan <xref:System.Windows.Forms.Control>. <xref:System.Windows.Forms.Control> Sınıfın tüm temel işlevleri (örneğin, olayları) denetimleri tarafından gerekli ancak hiçbir özel denetim işlevleri veya grafik arabirim sağlar. Bir denetimi devralarak oluşturma <xref:System.Windows.Forms.Control> sınıfı daha birçok düşünce ve kullanıcı denetimi ya da mevcut bir Windows Forms denetimi devralan daha çaba gerektirir. Yazar için kod yazmanız gereken <xref:System.Windows.Forms.Control.OnPaint%2A> gerekli işlevselliği belirli kod yanı sıra denetim olayı. Daha fazla esneklik, ancak izin verilir ve özel uyarlama bir denetim tam ihtiyaçlarınıza uyacak şekilde kurtarabilirsiniz. Örnek bir özel denetimin görünümünü ve bir analog saat eylemi yineleme saati denetimidir. Özel boyama yanıt olarak taşımak için saat kullanımına neden çağrılacak <xref:System.Windows.Forms.Timer.Tick> olayları iç zamanlayıcı bileşeni.  
  
 Devralınan <xref:System.Windows.Forms.Control> , sınıf:  
  
-   Özel bir grafik gösterimi denetiminizin sunmak istiyorsunuz.  
  
-   Standart denetimler kullanılabilir olmayan özel işlevselliği uygulamak gerekir.  
  
-   [Nasıl yapılır: Bir denetimi görüntüleme araç kutusu öğelerini Seç iletişim kutusu](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)  
  
-   [İzlenecek yol: DesignerSerializationVisibilityAttribute ile standart türler koleksiyonlarının seri hale getirme](serializing-collections-designerserializationvisibilityattribute.md)  
  
-   [İzlenecek yol: Visual C# ile Windows Forms Denetimi'nden devralma](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)  
  
-   [Nasıl yapılır: Bir denetim için araç kutusu bit eşlemi sağlama](how-to-provide-a-toolbox-bitmap-for-a-control.md)  
  
-   [Nasıl yapılır: Mevcut Windows Formları denetimlerinden devralma](how-to-inherit-from-existing-windows-forms-controls.md)  
  
-   [İzlenecek yol: Hata ayıklama özel Windows Forms denetimleri tasarım zamanında](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)  
  
-   [Nasıl yapılır: Denetim sınıfından devralma](how-to-inherit-from-the-control-class.md)  
  
-   [Nasıl yapılır: Bir UserControl denetiminin çalışma zamanı davranışını sınama](how-to-test-the-run-time-behavior-of-a-usercontrol.md)  
  
-   [Nasıl yapılır: Tasarım zamanında denetimi formların kenarlarına hizalama](how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)  
  
-   [Nasıl yapılır: UserControl sınıfından devralma](how-to-inherit-from-the-usercontrol-class.md)  
  
-   [Nasıl yapılır: Windows Forms için yazar denetimleri](how-to-author-controls-for-windows-forms.md)  
  
-   [Nasıl yapılır: Bileşik denetimler yazma](how-to-author-composite-controls.md)  
  
-   [İzlenecek yol: Visual Basic ile bileşik denetim yazma](walkthrough-authoring-a-composite-control-with-visual-basic.md)  
  
-   [İzlenecek yol: Visual C# ile bileşik denetim yazma](walkthrough-authoring-a-composite-control-with-visual-csharp.md)  
  
-   [İzlenecek yol: Visual Basic ile Windows Forms Denetimi'nden devralma](walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)  
  
-   [İzlenecek yol: Visual Studio tasarım zamanı özelliklerinden faydalanan Windows Forms denetimi oluşturma](creating-a-wf-control-design-time-features.md)  
  
-   [Nasıl yapılır: Tasarım zamanı özelliklerinden faydalanan Windows Forms denetimi oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: Basit bir Windows Forms denetimi geliştirme](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md)
- [Özel Denetim Çeşitleri](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
