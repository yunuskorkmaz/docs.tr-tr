---
title: Denetim Türü Önerileri
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- user controls [Windows Forms], when to use
- custom controls [Windows Forms], types
- controls [Windows Forms], creating
ms.assetid: 5235fe9d-c36a-4c08-ae76-6cb90b50085e
ms.openlocfilehash: fba10de27f7ba6f4c799d2110acd87394b7dbc95
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015995"
---
# <a name="control-type-recommendations"></a>Denetim Türü Önerileri

.NET Framework, yeni denetimler geliştirmek ve uygulamak için size güç sağlar. Tanıdık kullanıcı denetimine ek olarak, kendi boyamayı gerçekleştiren özel denetimler yazabileceksiniz ve varolan denetimlerin işlevselliğini devralma yoluyla genişletebiliyorsunuzdur. Oluşturulacak denetim türü kafa karıştırıcı olabilir. Bu bölümde, içinden kalıtımla alabileceğiniz çeşitli denetim türleri arasındaki farklar vurgulanmıştır ve projeniz için seçim yapmak üzere türle ilgili hususlar verilmektedir.

> [!NOTE]
> Web Forms üzerinde kullanmak üzere bir denetim yazmak istiyorsanız bkz. [özel ASP.NET Server denetimleri geliştirme](https://docs.microsoft.com/previous-versions/aspnet/zt27tfhy(v=vs.100)).

## <a name="inheriting-from-a-windows-forms-control"></a>Windows Forms denetiminden devralma

Devralınan bir denetimi, varolan bir Windows Forms denetiminden türetebilirsiniz. Bu yaklaşım, bir Windows Forms denetiminin tüm özelliklerini korumanızı ve sonra özel özellikler, Yöntemler veya diğer işlevler ekleyerek bu işlevselliği genişletmenizi sağlar. Örneğin, öğesinden <xref:System.Windows.Forms.TextBox> türetilmiş bir denetim oluşturabilirsiniz ve yalnızca sayıları kabul edebilir ve girişi otomatik olarak bir değere dönüştürür. Bu tür bir denetim, metin kutusundaki metin değiştiğinde çağrılan doğrulama kodunu içerebilir ve ek bir özellik, değer olabilir. Bazı denetimlerde, taban sınıfının <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemini geçersiz kılarak denetiminizin grafik arabirimine özel bir görünüm de ekleyebilirsiniz.

 Şu durumlarda Windows Forms denetiminden devralma:

- İhtiyacınız olan işlevlerin çoğu, mevcut bir Windows Forms denetimiyle zaten benzerdir.

- Özel bir grafik arabirimine ihtiyacınız yoktur ya da var olan bir denetim için yeni bir grafik ön ucu tasarlamak istiyorsunuz.

## <a name="inheriting-from-the-usercontrol-class"></a>UserControl sınıfından devralma

Kullanıcı denetimi, ortak bir kapsayıcıya kapsüllenmiş Windows Forms denetimleri koleksiyonudur. Kapsayıcı, Windows Forms denetimlerinin her biriyle ilişkili tüm işlevleri barındırır ve özelliklerini seçmeli olarak kullanıma sunma ve bağlama olanağı sağlar. Kullanıcı denetimine bir örnek, bir veritabanından müşteri adresi verilerini göstermek için oluşturulmuş bir denetim olabilir. Bu denetim, her alanın görüntülenmesi için birkaç metin kutuları ve kayıtlar arasında gezinmek için düğme denetimleri içerir. Veri bağlama özellikleri seçilerek gösterilebilir ve tüm denetim paketlenmiş ve uygulamadan uygulamaya yeniden kullanılabilir.

Şu durumlarda sınıfından al: <xref:System.Windows.Forms.UserControl>

- Birkaç Windows Forms denetiminin işlevselliğini tek bir yeniden kullanılabilir birimde birleştirmek istiyorsunuz.

## <a name="inheriting-from-the-control-class"></a>Denetim sınıfından devralma

Bir denetimi oluşturmanın başka bir yolu, öğesinden <xref:System.Windows.Forms.Control>devralarak sıfırdan önemli bir değer oluşturmaktır. <xref:System.Windows.Forms.Control> Sınıfı denetimler için gereken tüm temel işlevleri sağlar (örneğin, olaylar), ancak denetime özgü bir işlev veya grafik arabirimi yoktur. <xref:System.Windows.Forms.Control> Sınıfından devralarak bir denetim oluşturmak, kullanıcı denetiminden veya var olan bir Windows Forms denetiminden devralma işleminden daha fazla düşünce ve çaba gerektirir. Yazar, denetimin <xref:System.Windows.Forms.Control.OnPaint%2A> olayı için kod ve gerekli işlevselliğe özgü kod yazmalıdır. Ancak, daha fazla esnekliğe izin verilir, ancak bir denetimi tam olarak gereksinimlerinize uyacak şekilde özel olarak uyarlayabilirsiniz. Özel denetime örnek olarak, bir analog saatin görünümünü ve eylemini çoğaltan bir saat denetimidir. Özel boyama, saatin bir iç Zamanlayıcı bileşeninden gelen <xref:System.Windows.Forms.Timer.Tick> olaylara yanıt olarak taşınmasını sağlamak için çağrılabilir.

Şu durumlarda sınıfından al: <xref:System.Windows.Forms.Control>

- Denetiminizin özel bir grafik temsilini sağlamak istiyorsunuz.

- Standart denetimler aracılığıyla kullanılamayan özel işlevleri uygulamanız gerekir.

## <a name="related-articles"></a>İlgili makaleler

- [Nasıl yapılır: Araç kutusu öğelerini Seç Iletişim kutusunda bir denetim görüntüle](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)

- [İzlenecek yol: DesignerSerializationVisibilityAttribute ile standart türlerin koleksiyonlarını serileştirme](serializing-collections-designerserializationvisibilityattribute.md)

- [İzlenecek yol: Windows Forms denetiminden devralma](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)

- [Nasıl yapılır: Denetim için araç kutusu bit eşlemi sağlama](how-to-provide-a-toolbox-bitmap-for-a-control.md)

- [Nasıl yapılır: Mevcut Windows Forms denetimlerinden devralma](how-to-inherit-from-existing-windows-forms-controls.md)

- [İzlenecek yol: Tasarım zamanında özel Windows Forms Denetimlerinde hata ayıklama](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)

- [Nasıl yapılır: Denetim sınıfından devralma](how-to-inherit-from-the-control-class.md)

- [Nasıl yapılır: UserControl 'un çalışma zamanı davranışını test etme](how-to-test-the-run-time-behavior-of-a-usercontrol.md)

- [Nasıl yapılır: Tasarım zamanında form kenarlarına bir denetim hizalayın](how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)

- [Nasıl yapılır: UserControl sınıfından devralma](how-to-inherit-from-the-usercontrol-class.md)

- [Nasıl yapılır: Windows Forms için yazar denetimleri](how-to-author-controls-for-windows-forms.md)

- [Nasıl yapılır: Bileşik denetimleri yaz](how-to-author-composite-controls.md)

- [İzlenecek yol: Bileşik denetim yazma](walkthrough-authoring-a-composite-control-with-visual-csharp.md)

- [İzlenecek yol: Visual Studio tasarım zamanı özelliklerinden faydalanan bir Windows Forms denetimi oluşturma](creating-a-wf-control-design-time-features.md)

- [Nasıl yapılır: Tasarım zamanı özelliklerinden faydalanan bir Windows Forms denetimi oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Basit bir Windows Forms denetimi geliştirme](how-to-develop-a-simple-windows-forms-control.md)
- [Özel Denetim Çeşitleri](varieties-of-custom-controls.md)
