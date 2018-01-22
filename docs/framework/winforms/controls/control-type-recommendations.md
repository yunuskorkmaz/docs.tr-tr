---
title: "Denetim Türü Önerileri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- user controls [Windows Forms], when to use
- custom controls [Windows Forms], types
- controls [Windows Forms], creating
ms.assetid: 5235fe9d-c36a-4c08-ae76-6cb90b50085e
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a126d3b21ddd4bd31e168726c3538de21fb7d956
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="control-type-recommendations"></a>Denetim Türü Önerileri
.NET Framework verir geliştirmek ve yeni denetimler uygulamak için güç. Tanıdık kullanıcı denetimi yanı sıra kendi boyama gerçekleştirmek ve devralma yoluyla mevcut denetimleri işlevselliğini genişletmek bile mümkün olan özel denetimler yazabilmesi şimdi bulacaksınız. Karar denetimi oluşturmak için hangi tür kafa karıştırıcı olabilir. Bu bölüm, çeşitli içinden denetimleri arasındaki devrettiği ve projeniz için göz önünde bulundurularak seçmek için türü verir farklılıkları vurgular.  
  
> [!NOTE]
>  Web Forms kullanmak için bkz: bir denetim yazmak istiyorsanız [özel ASP.NET sunucu denetimleri geliştirme](http://msdn.microsoft.com/library/fbe26c16-cff4-4089-b3dd-877411f0c0ef).  
  
## <a name="inheriting-from-a-windows-forms-control"></a>Devralan bir Windows Forms denetimi  
 Varolan bir Windows Forms denetimden devralınan bir denetim türetilemeyeceğini. Bu yaklaşım, bir Windows Forms denetiminin devralınmış işlevselliğin korumak ve ardından özel özellikler, yöntemleri ve diğer işlevleri ekleyerek bu işlevselliği genişletmek için sağlar. Örneğin, türetilmiş bir denetim oluşturabilirsiniz <xref:System.Windows.Forms.TextBox> yalnızca sayı kabul edebilir ve otomatik olarak dönüştürür giriş değerini dönüştürür. Böyle bir denetim metin kutusundaki metin değiştirildi ve bir ek özellik olabilir her çağrıldı doğrulama kodu içerebilir değeri. Bazı denetimler de bir özel görünüm denetiminizi grafik arabirimine geçersiz kılarak ekleyebilirsiniz <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi temel sınıf.  
  
 Windows Forms denetimden devralır:  
  
-   Gereksinim duyduğunuz işlevselliği çoğunu zaten varolan bir Windows Forms denetimi aynı.  
  
-   Özel bir grafik arabirim gerekmez veya varolan bir denetim için yeni bir grafik ön uç tasarlamak istersiniz.  
  
## <a name="inheriting-from-the-usercontrol-class"></a>UserControl sınıfından devralma  
 Bir kullanıcı denetimi, ortak bir kapsayıcıya kapsüllenmiş Windows Forms denetimleri koleksiyonudur. Kapsayıcı tüm her Windows Forms denetimleri ile ilişkili devralınmış işlevselliğini içerir ve seçmeli olarak kullanıma sunmak ve bunların özelliklerini bağlayın olanak sağlar. Bir kullanıcı denetimi örneği bir veritabanı müşteri adresi verileri görüntülemek için yerleşik bir denetim olabilir. Bu denetim için her alan ve kayıtlarında gezinmek için düğmesi denetimleri birkaç metin kutuları içerir. Veri bağlama özellikleri seçmeli olarak açığa çıkabileceği ve tüm denetim paketlenir ve uygulamadan uygulamaya yeniden kullanılabilir.  
  
 Devralınan <xref:System.Windows.Forms.UserControl> varsa sınıfı:  
  
-   Çeşitli Windows Forms denetimleri işlevlerini tek bir yeniden kullanılabilir birime birleştirmek istediğiniz.  
  
## <a name="inheriting-from-the-control-class"></a>Denetim sınıfından devralma  
 Bir denetim oluşturmak için başka bir önemli ölçüde sıfırdan devralarak oluşturmak için yoludur <xref:System.Windows.Forms.Control>. <xref:System.Windows.Forms.Control> Sınıfı, tüm denetimler (örneğin, olayları) tarafından gereken temel işlevleri ancak hiçbir denetim özgü işlevsellik ya da grafik arabirim sağlar. Bir denetimi devralarak oluşturma <xref:System.Windows.Forms.Control> sınıfı, çok daha fazla düşünce ve kullanıcı denetimini veya varolan bir Windows Forms denetimi devralma daha çaba gerektirir. Yazar için kod yazmanız gerekir <xref:System.Windows.Forms.Control.OnPaint%2A> gerekli işlevselliği belirli kod yanı sıra denetim olayı. Daha fazla esneklik, ancak izin verilir ve özel uyarlama tam gereksinimlerinize uygun olarak bir kontrol edebilirsiniz. Özel bir denetimin görünümünü ve bir analog saat eylemi çoğaltan bir saat denetimi örneğidir. Özel boyama yanıt olarak taşımak için saatin ellerini neden çağrılacak <xref:System.Windows.Forms.Timer.Tick> bir iç süreölçer bileşeni olaylarından.  
  
 Devralınan <xref:System.Windows.Forms.Control> varsa sınıfı:  
  
-   Özel bir grafik gösterimi denetiminizin sağlamak istediğinizde.  
  
-   Standart denetimler kullanılabilir olmayan özel işlevsellik uygulamanız gerekir.  
  
-   [Nasıl yapılır: Araç Kutusu Öğelerini Seç İletişim Kutusunda bir Denetimi Görüntüleme](http://msdn.microsoft.com/library/9yxtkx75\(v=vs.110\))  
  
-   [İzlenecek yol: DesignerSerializationVisibilityAttribute ile Standart Türler Koleksiyonlarının Seri Hale Getirilmesi](http://msdn.microsoft.com/library/ms171731\(v=vs.110\))  
  
-   [İzlenecek yol: Visual C# ile beraber Windows Forms Denetimi'nden Devralma](http://msdn.microsoft.com/library/5h0k2e6x\(v=vs.110\))  
  
-   [Nasıl yapılır: Bir Denetim için Araç Kutusu Bit Eşlemi Sağlama](http://msdn.microsoft.com/library/4wk1wc0a\(v=vs.110\))  
  
-   [Nasıl yapılır: Mevcut Windows Forms Denetimlerinden Devralma](http://msdn.microsoft.com/library/7h62478z\(v=vs.110\))  
  
-   [İzlenecek yol: Tasarım Zamanında Özel Windows Forms Denetimleri Hatalarını Ayıklama](http://msdn.microsoft.com/library/5ytx0z24\(v=vs.110\))  
  
-   [Nasıl yapılır: Denetim Sınıfından Devralma](http://msdn.microsoft.com/library/skcysbt2\(v=vs.110\))  
  
-   [Nasıl yapılır: Bir UserControl Denetiminin Çalışma Zamanı Davranışını Sınama](http://msdn.microsoft.com/library/ms171738\(v=vs.110\))  
  
-   [Nasıl yapılır: Tasarım Zamanında Denetimi Formların Kenarlarına Hizalama](http://msdn.microsoft.com/library/1fxyb15b\(v=vs.110\))  
  
-   [Nasıl yapılır: UserControl Sınıfından Devralma](http://msdn.microsoft.com/library/00ctb4z0\(v=vs.110\))  
  
-   [Nasıl yapılır: Windows Forms için Denetimler Yazma](http://msdn.microsoft.com/library/bs3yhkh7\(v=vs.110\))  
  
-   [Nasıl yapılır: Bileşik Denetimler Yazma](http://msdn.microsoft.com/library/3sf86w5h\(v=vs.110\))  
  
-   [İzlenecek yol: Visual Basic İle Bileşik Denetim Yazma](http://msdn.microsoft.com/library/c316f119\(v=vs.110\))  
  
-   [İzlenecek yol: Visual C# İle Bileşik Denetim Yazma](http://msdn.microsoft.com/library/a6h7e207\(v=vs.110\))  
  
-   [İzlenecek yol: Visual Basic ile beraber Windows Forms Denetimi'nden Devralma](http://msdn.microsoft.com/library/w2a8y03d\(v=vs.110\))  
  
-   [Nasıl yapılır: tasarım-zamanı özellikleri yararlanan bir Windows Forms denetimi oluşturma](http://msdn.microsoft.com/library/307hck25\(v=vs.110\))  
  
-   [Nasıl yapılır: tasarım-zamanı özellikleri yararlanan bir Windows Forms denetimi oluşturma](http://msdn.microsoft.com/library/307hck25\(v=vs.120\))  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: Basit Bir Windows Forms Denetimi Geliştirme](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md)  
 [Özel Denetim Çeşitleri](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
