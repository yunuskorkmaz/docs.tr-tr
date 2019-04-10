---
title: 'İzlenecek yol: Visual Basic ile COM nesneleri oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop [Visual Basic], creating COM objects
- COM objects, creating
- COM interop [Visual Basic], walkthroughs
- object creation [Visual Basic], COM objects
- COM objects, walkthroughs
ms.assetid: 7b07a463-bc72-4392-9ba0-9dfcb697a44f
ms.openlocfilehash: 97e917d568b31860979e54598350d1ae7a6fdb25
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59331903"
---
# <a name="walkthrough-creating-com-objects-with-visual-basic"></a>İzlenecek yol: Visual Basic ile COM nesneleri oluşturma
Yeni uygulama veya bileşenler oluştururken, .NET Framework derlemeleri oluşturmak idealdir. Ancak, Visual Basic ayrıca, bir .NET Framework bileşenini vystavit kullanıma sunmak kolaylaştırır Bu yeni bileşenler için COM bileşenlerini gerektiren önceki uygulama paketlerini vermenizi sağlar. Bu izlenecek yol göstermek için Visual Basic kullanmayı gösteren [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] nesneler COM nesneleri, hem ile hem de olmadan COM sınıf şablonu olarak.  
  
 COM nesnelerini kullanıma sunmak için en kolay yolu, COM sınıf şablonu kullanmaktır. COM sınıf şablonu, yeni bir sınıf oluşturur ve projenize bir COM nesnesi olarak sınıfı ve birlikte çalışabilirlik katman oluşturmak ve işletim sistemi ile kaydetmek için yapılandırır.  
  
> [!NOTE]
>  Visual Basic'te kullanmak için yönetilmeyen kod için bir COM nesnesi olarak oluşturulmuş bir sınıf görülebileceği da olsa da, doğru bir COM nesnesi değil ve Visual Basic tarafından kullanılamaz. Daha fazla bilgi için [.NET Framework uygulamalarında COM birlikte çalışabilirliği](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-com-object-by-using-the-com-class-template"></a>COM sınıf şablonu kullanarak bir COM nesnesi oluşturmak için  
  
1. Yeni bir Windows uygulaması projesi açın **dosya** tıklayarak menü **yeni proje**.  
  
2. İçinde **yeni proje** iletişim kutusunun altında **proje türleri** alan, Windows seçili olup olmadığını denetleyin. Seçin **sınıf kitaplığı** gelen **şablonları** listeleyin ve ardından **Tamam**. Yeni Proje görüntülenir.  
  
3. Seçin **Yeni Öğe Ekle** gelen **proje** menüsü. **Yeni Öğe Ekle** iletişim kutusu görüntülenir.  
  
4. Seçin **COM sınıfı** gelen **şablonları** listeleyin ve ardından **Ekle**. Visual Basic, yeni bir sınıf ekler ve yeni proje COM birlikte çalışması için yapılandırır.  
  
5. Kod gibi özellikleri, yöntemleri ve olayları COM sınıfına ekleyin.  
  
6. Seçin **derleme ClassLibrary1** gelen **derleme** menüsü. Visual Basic derleme yapıları ve COM nesnesi işletim sistemi ile kaydeder.  
  
## <a name="creating-com-objects-without-the-com-class-template"></a>COM sınıf şablonu olmadan COM nesneleri oluşturma  
 Ayrıca, bir COM sınıfı COM sınıf şablonu kullanmak yerine el ile oluşturabilirsiniz. Bu yordam, komut satırından çalışırken veya COM nesnelerinin nasıl tanımlandığı hakkında daha fazla denetime istediğinizde yararlıdır.  
  
#### <a name="to-set-up-your-project-to-generate-a-com-object"></a>Bir COM nesnesi oluşturmak için projenizi ayarlamak için  
  
1. Yeni bir Windows uygulaması projesi açın **dosya** tıklayarak menü **NewProject**.  
  
2. İçinde **yeni proje** iletişim kutusunun altında **proje türleri** alan, Windows seçili olup olmadığını denetleyin. Seçin **sınıf kitaplığı** gelen **şablonları** listeleyin ve ardından **Tamam**. Yeni Proje görüntülenir.  
  
3. İçinde **Çözüm Gezgini**, projenize sağ tıklayın ve ardından **özellikleri**. **Proje Tasarımcısı** görüntülenir.  
  
4. Tıklayın **derleme** sekmesi.  
  
5. Seçin **kaydetme COM birlikte çalışması için** onay kutusu.  
  
#### <a name="to-set-up-the-code-in-your-class-to-create-a-com-object"></a>Bir COM nesnesi oluşturmak için kod Sınıfınız içinde ayarlamak için  
  
1. İçinde **Çözüm Gezgini**, çift **Class1.vb** kodunu görüntülemek için.  
  
2. Sınıfı Yeniden Adlandır `ComClass1`.  
  
3. Aşağıdaki sabitleri ekleyin `ComClass1`. Bunlar, COM nesneleri için gerekli olan genel benzersiz tanıtıcısı (GUID) sabitleri depolar.  
  
     [!code-vb[VbVbalrInterop#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#2)]  
  
4. Üzerinde **Araçları** menüsünü tıklatın **GUID Oluştur**. İçinde **GUID Oluştur** iletişim kutusu, tıklayın **biçimi kayıt defteri** ve ardından **kopyalama**. **Çıkış**'a tıklayın.  
  
5. Boş bir dize yerine `ClassId` başında kaldırma ve sondaki GUID ile küme ayraçları. Örneğin, GUID GUIDgen tarafından sağlanmışsa `"{2C8B0AEE-02C9-486e-B809-C780A11530FE}"` sonra kodunuzu aşağıdaki gibi görünmelidir.  
  
     [!code-vb[VbVbalrInterop#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#3)]  
  
6. Önceki adımları yineleyin `InterfaceId` ve `EventsId` sabitleri, aşağıdaki örnekte olduğu gibi.  
  
     [!code-vb[VbVbalrInterop#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#4)]  
  
    > [!NOTE]
    >  GUID'ler yeni ve benzersiz olduğundan emin olun; Aksi takdirde, COM bileşeni ile diğer COM bileşenleri çakışabilir.  
  
7. Ekleme `ComClass` özniteliğini `ComClass1`, aşağıdaki örnekte olduğu gibi sınıf kimliği, arabirim kimliği ve olay kimliği GUID'leri belirtme:  
  
     [!code-vb[VbVbalrInterop#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#5)]  
  
8. COM sınıfları bir parametresiz olmalıdır `Public Sub New()` Oluşturucusu veya sınıf kaydetme doğru. Parametresiz bir oluşturucu, sınıfı ekleyin:  
  
     [!code-vb[VbVbalrInterop#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#6)]  
  
9. İle biten sınıfı özellikleri, yöntemleri ve olayları eklemek bir `End Class` deyimi. Seçin **Çözümü Derle** gelen **derleme** menüsü. Visual Basic derleme yapıları ve COM nesnesi işletim sistemi ile kaydeder.  
  
    > [!NOTE]
    >  COM nesneleri doğru olmadığı için Visual Basic ile oluşturduğunuz COM nesneleri başka bir Visual Basic uygulama tarafından kullanılamaz. Bu tür COM nesnelerine başvurular ekleme girişimleri hata oluşturur. Ayrıntılar için bkz [.NET Framework uygulamalarında COM birlikte çalışabilirliği](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.ComClassAttribute>
- [COM Birlikte Çalışma](../../../visual-basic/programming-guide/com-interop/index.md)
- [İzlenecek yol: COM nesnelerinde kalıtım uygulama](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)
- [#Region Yönergesi](../../../visual-basic/language-reference/directives/region-directive.md)
- [.NET Framework Uygulamalarında COM Birlikte Çalışabilirliği](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)
- [Birlikte Çalışabilirlik İle İlgili Sorun Giderme](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)
