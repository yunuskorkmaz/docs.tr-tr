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
ms.openlocfilehash: 43ba068663db9f8c3816a6f731395a6682a130e6
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91083299"
---
# <a name="how-to-reference-com-objects-from-visual-basic"></a>Nasıl yapılır: Visual Basic'den COM Nesnelerine Başvuru Yapma

Visual Basic, tür kitaplıklarının bulunduğu COM nesnelerine başvurular eklemek için COM kitaplığı için birlikte çalışma derlemesinin oluşturulması gerekir. COM nesnesinin üyelerine yapılan başvurular birlikte çalışma derlemesine yönlendirilir ve ardından gerçek COM nesnesine iletilir. COM nesnesinden gelen yanıtlar birlikte çalışma derlemesine yönlendirilir ve .NET Framework uygulamanıza iletilir.  
  
 Bir .NET derlemesine COM nesnesinin tür bilgilerini gömerek derleme kullanmadan bir COM nesnesine başvurabilirsiniz. Tür bilgilerini eklemek için `Embed Interop Types` ÖZELLIĞI `True` com nesnesine başvuru için olarak ayarlayın. Komut satırı derleyicisini kullanarak derlerken, `/link` com kitaplığına başvurmak için seçeneğini kullanın. Daha fazla bilgi için bkz. [-Link (Visual Basic)](../../reference/command-line-compiler/link.md).  
  
 Visual Basic, tümleşik geliştirme ortamından (IDE) bir tür kitaplığına bir başvuru eklediğinizde otomatik olarak birlikte çalışma derlemeleri oluşturur. Komut satırından çalışırken, Tlbimp yardımcı programını kullanarak birlikte çalışma derlemelerini el ile oluşturabilirsiniz.  
  
### <a name="to-add-references-to-com-objects"></a>COM nesnelerine başvuru eklemek için  
  
1. **Proje** menüsünde, **Başvuru Ekle** ' yi seçin ve ardından iletişim kutusunda **com** sekmesine tıklayın.  
  
2. COM nesneleri listesinden kullanmak istediğiniz bileşeni seçin.  
  
3. Birlikte çalışma derlemesine erişimi basitleştirmek için, `Imports` com nesnesini kullanacağınız sınıfın veya modülün üst kısmına bir ifade ekleyin. Örneğin, aşağıdaki kod örneği, `INKEDLib` kitaplıkta başvurulan nesneler için ad alanını içeri aktarır `Microsoft InkEdit Control 1.0` .  
  
     [!code-vb[VbVbalrInterop#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#40)]  
  
### <a name="to-create-an-interop-assembly-using-tlbimp"></a>Tlbimp kullanarak birlikte çalışma derlemesi oluşturmak için  
  
1. Tlbimp 'nin konumunu, zaten arama yolunun bir parçası değilse ve şu anda bulunduğu dizinde değilseniz arama yoluna ekleyin.  
  
2. Aşağıdaki bilgileri sağlayarak bir komut isteminden Tlbimp 'i çağırın:  
  
    - Tür kitaplığını içeren DLL 'nin adı ve konumu  
  
    - Bilgilerin yerleştirilmesi gereken ad alanının adı ve konumu  
  
    - Hedef birlikte çalışma derlemesinin adı ve konumu  
  
     Aşağıdaki kod bir örnek sağlar:  
  
    ```console  
    Tlbimp test3.dll /out:NameSpace1 /out:Interop1.dll  
    ```  
  
     Kayıtsız COM nesneleri için bile tür kitaplıkları için birlikte çalışma derlemeleri oluşturmak üzere Tlbimp kullanabilirsiniz. Bununla birlikte, birlikte çalışma derlemelerinin başvurduğu COM nesneleri, kullanıldığı bilgisayarda düzgün şekilde kaydedilmelidir. Windows işletim sistemine dahil edilen regsvr32 yardımcı programını kullanarak bir COM nesnesini kaydedebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [COM birlikte çalışma](index.md)
- [Tlbimp.exe (tür kitaplığı Içeri Aktarıcı)](../../../framework/tools/tlbimp-exe-type-library-importer.md)
- [Tlbexp.exe (tür kitaplığı verme programı)](../../../framework/tools/tlbexp-exe-type-library-exporter.md)
- [İzlenecek yol: COM Nesnelerinde Kalıtım Uygulama](walkthrough-implementing-inheritance-with-com-objects.md)
- [Birlikte Çalışabilirlik İle İlgili Sorun Giderme](troubleshooting-interoperability.md)
- [Imports Deyimi (.NET Ad Alanı ve Türü)](../../language-reference/statements/imports-statement-net-namespace-and-type.md)
