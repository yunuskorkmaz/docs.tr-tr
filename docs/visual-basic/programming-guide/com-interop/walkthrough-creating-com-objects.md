---
title: "İzlenecek yol: Visual Basic ile COM Nesneleri Oluşturma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- COM interop [Visual Basic], creating COM objects
- COM objects, creating
- COM interop [Visual Basic], walkthroughs
- object creation [Visual Basic], COM objects
- COM objects, walkthroughs
ms.assetid: 7b07a463-bc72-4392-9ba0-9dfcb697a44f
caps.latest.revision: "30"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ff7d3868a2e3ddaba06ebc6f98c8eacfc7299366
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-creating-com-objects-with-visual-basic"></a>İzlenecek yol: Visual Basic ile COM Nesneleri Oluşturma
Yeni uygulamalar veya bileşenleri oluştururken, .NET Framework derlemeleri oluşturma en iyisidir. Ancak, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] com .NET Framework bileşenine kullanıma sunmak kolaylaştırır Bu, COM bileşenlerini gerektiren önceki uygulama paketleri için yeni bileşenler sağlamanıza izin verir. Bu kılavuzda nasıl kullanılacağı ortaya [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kullanıma sunmak için [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] nesneleri COM nesneleri, hem ile hem de COM sınıfı şablonu olmadan olarak.  
  
 COM nesneleri kullanıma sunmak için en kolay yolu, COM sınıfı şablonu kullanmaktır. COM sınıfı şablonu yeni bir sınıf oluşturur ve projenizin COM nesnesi olarak sınıfı ve birlikte çalışabilirlik katmanı oluşturmak ve işletim sistemi ile kaydetmek için yapılandırır.  
  
> [!NOTE]
>  Oluşturulan sınıf ayrıca getirebilir rağmen [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kullanmak yönetilmeyen kod için bir COM nesnesi olarak doğru bir COM nesnesi değil ve tarafından kullanılamaz [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]. Daha fazla bilgi için bkz: [.NET Framework uygulamalarında COM birlikte çalışabilirliği](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-com-object-by-using-the-com-class-template"></a>COM sınıfı şablonu kullanarak bir COM nesnesi oluşturmak için  
  
1.  Yeni bir Windows uygulaması projesinden açın **dosya** menüsünde tıklayarak **yeni proje**.  
  
2.  İçinde **yeni proje** iletişim kutusunda altında **proje türleri** alan, Windows işaretli olup olmadığını denetleyin. Seçin **sınıf kitaplığı** gelen **şablonları** listeleyin ve ardından **Tamam**. Yeni Proje görüntülenir.  
  
3.  Seçin **Yeni Öğe Ekle** gelen **proje** menüsü. **Yeni Öğe Ekle** iletişim kutusu görüntülenir.  
  
4.  Seçin **COM sınıfı** gelen **şablonları** listeleyin ve ardından **Ekle**. [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]Yeni bir sınıf ekler ve yeni proje COM birlikte çalışma için yapılandırır.  
  
5.  Özellikleri, yöntemleri ve olayları gibi kodu COM sınıfına ekleyin.  
  
6.  Seçin **yapı ClassLibrary1** gelen **yapı** menüsü. [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]derleme oluşturur ve COM nesnesi işletim sistemi ile kaydeder.  
  
## <a name="creating-com-objects-without-the-com-class-template"></a>COM sınıfı şablonu olmadan COM nesneleri oluşturma  
 COM sınıfı şablonu kullanmak yerine el ile bir COM sınıfı de oluşturabilirsiniz. Bu yordam, komut satırından çalışırken veya COM nesneleri nasıl tanımlanan üzerinde daha fazla denetim istediğinizde yararlıdır.  
  
#### <a name="to-set-up-your-project-to-generate-a-com-object"></a>Bir COM nesnesi oluşturmak için projenizi ayarlamak için  
  
1.  Yeni bir Windows uygulaması projesinden açın **dosya** menüsünde tıklayarak **NewProject**.  
  
2.  İçinde **yeni proje** iletişim kutusunda altında **proje türleri** alan, Windows işaretli olup olmadığını denetleyin. Seçin **sınıf kitaplığı** gelen **şablonları** listeleyin ve ardından **Tamam**. Yeni Proje görüntülenir.  
  
3.  İçinde **Çözüm Gezgini**, projenize sağ tıklayın ve ardından **özellikleri**. **Proje Tasarımcısı** görüntülenir.  
  
4.  Tıklatın **derleme** sekmesi.  
  
5.  Seçin **kaydetmek için COM birlikte çalışma** onay kutusu.  
  
#### <a name="to-set-up-the-code-in-your-class-to-create-a-com-object"></a>Bir COM nesnesi oluşturmak için kod sınıfınızda ayarlamak için  
  
1.  İçinde **Çözüm Gezgini**, çift **Class1.vb'ye** kendi kodumu görüntülemek için.  
  
2.  Sınıfı için yeniden adlandırma `ComClass1`.  
  
3.  Aşağıdaki sabitleri ekleyin `ComClass1`. Bunlar COM nesneleri sahip olması gereken genel benzersiz tanımlayıcı (GUID) sabitleri depolar.  
  
     [!code-vb[VbVbalrInterop#2](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_1.vb)]  
  
4.  Üzerinde **Araçları** menüsünde tıklatın **Create GUID**. İçinde **Create GUID** iletişim kutusu, tıklatın **kayıt defteri biçimi** ve ardından **kopya**. **Çıkış**'a tıklayın.  
  
5.  Boş dize Değiştir `ClassId` kaldırarak başında ve sonunda GUID ile küme ayraçları. Örneğin, GUID GUIDgen tarafından sağlanan ise `"{2C8B0AEE-02C9-486e-B809-C780A11530FE}"` sonra kodunuzu aşağıdaki gibi görünmelidir.  
  
     [!code-vb[VbVbalrInterop#3](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_2.vb)]  
  
6.  İçin önceki adımı yineleyin `InterfaceId` ve `EventsId` aşağıdaki örnekteki gibi sabitleri.  
  
     [!code-vb[VbVbalrInterop#4](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_3.vb)]  
  
    > [!NOTE]
    >  GUID'lerin yeni ve benzersiz olduğundan emin olun; Aksi takdirde, COM bileşeni diğer COM bileşenleri ile çakışıyor.  
  
7.  Ekleme `ComClass` özniteliğini `ComClass1`, GUID'lerini aşağıdaki örnekteki sınıfı kimliği, arabirim kimliği ve olayları kimliği belirtme:  
  
     [!code-vb[VbVbalrInterop#5](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_4.vb)]  
  
8.  COM sınıfları bir parametresiz olmalıdır `Public Sub New()` Oluşturucusu veya sınıfın kaydettirilemedi doğru. Parametresiz bir kurucusu sınıfına ekleyin:  
  
     [!code-vb[VbVbalrInterop#6](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_5.vb)]  
  
9. Özellikleri, yöntemleri ve olayları ile biten sınıfına ekleyin bir `End Class` deyimi. Seçin **yapı çözümü** gelen **yapı** menüsü. [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]derleme oluşturur ve COM nesnesi işletim sistemi ile kaydeder.  
  
    > [!NOTE]
    >  Oluşturduğunuz ile COM nesneleri [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] diğer kullanılamaz [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] uygulamaları true COM nesneleri olmadıklarından. Bu tür COM nesnelerine başvurular ekleme girişimleri bir hata ortaya koyar. Ayrıntılar için bkz [.NET Framework uygulamalarında COM birlikte çalışabilirliği](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.ComClassAttribute>  
 [COM birlikte çalışma](../../../visual-basic/programming-guide/com-interop/index.md)  
 [İzlenecek yol: COM nesnelerinde kalıtım uygulama](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)  
 [#Region yönergesi](../../../visual-basic/language-reference/directives/region-directive.md)  
 [.NET Framework uygulamalarında COM birlikte çalışabilirliği](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)  
 [Birlikte çalışabilirlik sorunlarını giderme](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)
