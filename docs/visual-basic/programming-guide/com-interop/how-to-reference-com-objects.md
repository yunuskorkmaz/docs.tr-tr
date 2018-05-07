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
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-reference-com-objects-from-visual-basic"></a>Nasıl yapılır: Visual Basic'den COM Nesnelerine Başvuru Yapma
Visual Basic'te tür kitaplıklarının COM nesneleri başvuruları ekleme birlikte çalışabilirlik bütünleştirilmiş oluşturulması için COM kitaplığı gerektirir. COM Nesne üyeleri için başvurular birlikte çalışma derlemesine yönlendirilir ve gerçek COM nesneye iletilir. COM nesnesi yanıtlarının birlikte çalışma derlemesine yönlendirilir ve iletilir, [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] uygulama.  
  
 Bir .NET derlemesi COM nesnesinin tür bilgilerini katıştırma ile birlikte çalışma bütünleştirilmiş kullanmadan bir COM nesnesi başvuruda bulunabilir. Tür bilgileri katıştırmak için `Embed Interop Types` özelliğine `True` COM Nesne başvurusunu için. Komut satırı derleyicisini kullanarak derlediğiniz kullanırsanız `/link` COM kitaplığı başvurusu için seçeneği. Daha fazla bilgi için bkz: [/Link (Visual Basic)](../../../visual-basic/reference/command-line-compiler/link.md).  
  
 Tümleşik geliştirme ortamı (IDE) bir tür kitaplığı için bir başvuru eklediğinizde, Visual Basic birlikte çalışma derlemeleri otomatik olarak oluşturur. Komut satırından çalışırken, el ile birlikte çalışma derlemeleri oluşturma için Tlbimp yardımcı programını kullanabilirsiniz.  
  
### <a name="to-add-references-to-com-objects"></a>COM nesneleri eklemek için  
  
1.  Üzerinde **proje** menüsünde seçin **Başvuru Ekle** ve ardından **COM** iletişim kutusundaki sekmesi.  
  
2.  COM nesneleri listesinden kullanmak istediğiniz bileşeni seçin.  
  
3.  Birlikte çalışma derlemesi erişimi kolaylaştırmak için add bir `Imports` sınıfı veya COM nesnesi içinde kullanacağınız modülü üstüne deyimi. Örneğin, aşağıdaki kod örneğinde ad alır `INKEDLib` başvurulan nesneler için `Microsoft InkEdit Control 1.0` kitaplığı.  
  
     [!code-vb[VbVbalrInterop#40](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/how-to-reference-com-objects_1.vb)]  
  
### <a name="to-create-an-interop-assembly-using-tlbimp"></a>Birlikte çalışma bütünleştirilmiş Tlbimp kullanarak oluşturmak için  
  
1.  Bunu zaten arama yolu parçası olmayan ve, şu anda bulunduğu dizinde olmayan Tlbimp konumunu arama yoluna ekleyin.  
  
2.  Çağrı, bir komut isteminden aşağıdaki bilgileri sağlayarak Tlbimp:  
  
    -   Ad ve tür kitaplığı içeren dll Dosyasının konumu  
  
    -   Ad ve konum bilgileri nereye yerleştirileceğini ad alanı  
  
    -   Ad ve konum hedef birlikte çalışma derlemesinin  
  
     Aşağıdaki kod bir örnek sağlar:  
  
    ```  
    Tlbimp test3.dll /out:NameSpace1 /out:Interop1.dll  
    ```  
  
     Kayıtsız COM nesneleri için bile tür kitaplıkları için birlikte çalışma derlemeleri oluşturma için Tlbimp kullanabilirsiniz. Ancak, birlikte çalışma derlemeleri tarafından başvurulan COM nesneleri düzgün kullanılacak oldukları bilgisayarda kayıtlı olması gerekir. Bir COM nesnesi ile Windows işletim sisteminde Regsvr32 yardımcı programını kullanarak kaydedebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [COM Birlikte Çalışma](../../../visual-basic/programming-guide/com-interop/index.md)  
 [Tlbimp.exe (Tür Kitaplığı İçeri Aktarıcı)](../../../framework/tools/tlbimp-exe-type-library-importer.md)  
 [Tlbexp.exe (Tür Kitaplığı Dışarı Aktarıcı)](http://msdn.microsoft.com/library/a487d61b-d166-467b-a7ca-d8b52fbff42d)  
 [İzlenecek yol: COM Nesnelerinde Kalıtım Uygulama](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)  
 [Birlikte Çalışabilirlik İle İlgili Sorun Giderme](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)  
 [Imports Deyimi (.NET Ad Alanı ve Türü)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
