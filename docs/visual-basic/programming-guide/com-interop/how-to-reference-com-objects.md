---
title: "Nasıl yapılır: Visual Basic'den COM Nesnelerine Başvuru Yapma"
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop [Visual Basic], referencing COM objects
- referencing objects, COM objects from Visual Basic
- objects [Visual Basic], referencing
- COM objects, referencing
- interop assemblies
ms.assetid: 9c518fb4-27d9-4112-9e6a-5a7d0210af6f
ms.openlocfilehash: 49f3da396ca5cd48b0cf454ce1ecd5422c28e38f
ms.sourcegitcommit: 2d8b7488d94101b534ca3e9780b1c1e840233405
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2018
ms.locfileid: "39199371"
---
# <a name="how-to-reference-com-objects-from-visual-basic"></a>Nasıl yapılır: Visual Basic'den COM Nesnelerine Başvuru Yapma
Visual Basic'te tür kitaplıklarını sahip bir COM nesnelerine başvuru ekleme birlikte çalışma derlemesi oluşturulması için COM kitaplığı gerektirir. COM nesnesinin üyeleri için başvurular birlikte çalışma derlemesine yönlendirilir ve ardından gerçek COM nesneye iletilir. COM nesnesi alınan yanıtları birlikte çalışma derlemesine yönlendirilir ve iletilmesi, [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] uygulama.  
  
 Tür bilgilerini COM nesnesi için bir .NET derlemesine gömerek birlikte çalışma derlemesi kullanmadan bir COM nesnesi başvuruda bulunabilir. Tür bilgilerini katıştırma için ayarlanmış `Embed Interop Types` özelliğini `True` için COM nesnesine başvuru. Komut satırı derleyicisini kullanarak derlemek kullanırsanız `/link` COM kitaplığı başvurmak için seçeneği. Daha fazla bilgi için [/Link (Visual Basic)](../../../visual-basic/reference/command-line-compiler/link.md).  
  
 Tümleşik geliştirme ortamından (IDE) bir tür kitaplığına bir başvuru eklediğinizde, Visual Basic birlikte çalışma derlemeleri otomatik olarak oluşturur. Komut satırından çalışırken, birlikte çalışma derlemelerini el ile oluşturmak için Tlbimp yardımcı programını kullanabilirsiniz.  
  
### <a name="to-add-references-to-com-objects"></a>COM nesnelerinin başvuruları eklemek için  
  
1.  Üzerinde **proje** menüsünde seçin **Başvuru Ekle** ve ardından **COM** iletişim kutusundaki sekmesi.  
  
2.  COM nesneleri listesinden kullanmak istediğiniz bileşeni seçin.  
  
3.  Birlikte çalışma derlemesi erişimini basitleştirmek için ekleme bir `Imports` sınıfı veya modülü COM nesnesi içinde kullanacağınız üstüne deyimi. Örneğin, aşağıdaki kod örneği ad alanını içeri aktarır `INKEDLib` başvurulan nesneler için `Microsoft InkEdit Control 1.0` kitaplığı.  
  
     [!code-vb[VbVbalrInterop#40](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/how-to-reference-com-objects_1.vb)]  
  
### <a name="to-create-an-interop-assembly-using-tlbimp"></a>Tlbimp kullanarak birlikte çalışma derlemesi oluşturmak için  
  
1.  Tlbimp konumunu zaten arama yolu bir parçası değilse ve değil o anda bulunduğu dizinde arama yoluna ekleyin.  
  
2.  Çağrı, bir komut isteminden aşağıdaki bilgileri sağlayarak Tlbimp:  
  
    -   Ad ve tür kitaplığı içeren DLL konumunu  
  
    -   Ad ve konum bilgileri yerleştirilmesi gereken ad alanı  
  
    -   Ad ve hedef birlikte çalışma bütünleştirilmiş kod konumu  
  
     Aşağıdaki kod, bir örnek sağlar:  
  
    ```  
    Tlbimp test3.dll /out:NameSpace1 /out:Interop1.dll  
    ```  
  
     Kayıtsız COM nesneleri için bile, tür kitaplıkları için birlikte çalışma derlemeleri oluşturmak için Tlbimp kullanabilirsiniz. Ancak, birlikte çalışma derlemesi tarafından başvurulan COM nesneleri kullanılacak oldukları bilgisayarda düzgün bir şekilde kaydedilmesi gerekir. Bir COM nesnesi ile Windows işletim sisteminde Regsvr32 yardımcı programını kullanarak kaydedebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [COM Birlikte Çalışma](../../../visual-basic/programming-guide/com-interop/index.md)  
 [Tlbimp.exe (Tür Kitaplığı İçeri Aktarıcı)](../../../framework/tools/tlbimp-exe-type-library-importer.md)  
 [Tlbexp.exe (Tür Kitaplığı Dışarı Aktarıcı)](http://msdn.microsoft.com/library/a487d61b-d166-467b-a7ca-d8b52fbff42d)  
 [İzlenecek yol: COM Nesnelerinde Kalıtım Uygulama](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)  
 [Birlikte Çalışabilirlik İle İlgili Sorun Giderme](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)  
 [Imports Deyimi (.NET Ad Alanı ve Türü)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
