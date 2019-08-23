---
title: -bağlantı (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- l compiler option [Visual Basic]
- EmbedInteropTypes
- embed interop types [COM Interop]
- -link compiler option [Visual Basic]
- /link compiler option [Visual Basic]
- link compiler option [Visual Basic]
- -l compiler option [Visual Basic]
- /l compiler option [Visual Basic]
ms.assetid: 1885f24a-86f5-486c-a064-9fb7e455ccec
ms.openlocfilehash: fbce22755b3732896a226c00bbf8e068dc1f098e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929391"
---
# <a name="-link-visual-basic"></a>-bağlantı (Visual Basic)
Derleyicinin, belirtilen derlemelerdeki COM tür bilgilerini şu anda derlediğiniz projede kullanılabilir hale getirmesine neden olur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
-link:fileList  
' -or-  
-l:fileList  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terim|Tanım|  
|---|---|  
|`fileList`|Gerekli. Bütünleştirilmiş kod dosyası adlarının virgülle ayrılmış listesi. Dosya adı bir boşluk içeriyorsa, adı tırnak işaretleri içine alın.|  
  
## <a name="remarks"></a>Açıklamalar  
 `-link` Seçeneği, gömülü tür bilgilerine sahip bir uygulamayı dağıtmanıza olanak sağlar. Uygulama daha sonra, çalışma zamanı derlemesine bir başvuruya gerek duymadan gömülü tür bilgilerini uygulayan bir çalışma zamanı derlemesinde türleri kullanabilir. Çalışma zamanı derlemesinin çeşitli sürümleri yayımlanıyorsa, katıştırılmış tür bilgilerini içeren uygulama, yeniden derlenmesi gerekmeden çeşitli sürümlerle çalışabilir. Bir örnek için bkz [. İzlenecek yol: Yönetilen derlemelerden](../../../visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-vs.md)türler ekleme.  
  
 `-link` Seçeneğinin kullanılması özellikle com birlikte çalışabilirliğine çalışırken yararlıdır. Uygulamanızın artık hedef bilgisayarda bir birincil birlikte çalışma derlemesi (PIA) gerektirmemesi için COM türlerini katıştırabilirsiniz. `-link` Seçeneği, derleyicinin başvurulan birlikte çalışma derlemesindeki com tür bilgilerini sonuçta elde edilen derlenmiş koda katıştırmasını söyler. COM türü, CLSID (GUID) değeri tarafından tanımlanır. Sonuç olarak, uygulamanız aynı CLSID değerleriyle aynı COM türlerini yükleyen bir hedef bilgisayarda çalışabilir. Microsoft Office otomatikleştiren uygulamalar iyi bir örnektir. Office gibi uygulamalar genellikle farklı sürümlerde aynı CLSID değerini tutacağından, uygulamanız hedef bilgisayarda .NET Framework 4 veya sonraki bir sürüm yüklendiği sürece başvurulan COM türlerini kullanabilir ve uygulamanız Yöntemler, özellikler veya uygulamalar kullanır. başvurulan COM türlerine dahil edilen olaylar.  
  
 `-link` Seçeneği yalnızca arabirimleri, yapıları ve temsilcileri katıştırır. COM sınıfları ekleme desteklenmiyor.  
  
> [!NOTE]
> Kodunuzda gömülü bir COM türünün örneğini oluşturduğunuzda, uygun arabirimi kullanarak örneği oluşturmanız gerekir. CoClass kullanarak gömülü COM türünün bir örneğini oluşturma girişimi hataya neden olur.  
  
 Visual Studio 'da `-link` seçeneğini ayarlamak için bir derleme başvurusu ekleyin ve `Embed Interop Types` özelliği **true**olarak ayarlayın. `Embed Interop Types` Özelliği için varsayılan değer **false**'dur.  
  
 Başka bir COM derlemesine (derleme B) başvuran bir COM derlemesine (derleme A) bağlarsanız, aşağıdakilerden biri doğruysa derleme B 'ye de bağlantı oluşturmanız gerekir:  
  
- Derleme A 'dan bir tür bir türden devralınır veya derleme B 'den bir arabirim uygular.  
  
- B derlemesinden dönüş türü veya parametre türü olan bir alan, özellik, olay veya yöntem çağrılır.  
  
 Bir veya daha fazla derleme başvurularınızın bulunduğu dizini belirtmek için [-libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) kullanın.  
  
 [/Reference](../../../visual-basic/reference/command-line-compiler/reference.md) derleyici seçeneği gibi, `-link` derleyici seçeneği de sık kullanılan .NET Framework derlemelerine başvuran Vbc. rsp yanıt dosyasını kullanır. Derleyicinin Vbc. rsp dosyasını kullanmasını istemiyorsanız [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md) derleyici seçeneğini kullanın.  
  
 `-link` Öğesinin`-l`kısa biçimi.  
  
## <a name="generics-and-embedded-types"></a>Genel türler ve katıştırılmış türler  
 Aşağıdaki bölümlerde, birlikte çalışma türlerini gömün uygulamalarda genel türleri kullanma sınırlamaları açıklanır.  
  
### <a name="generic-interfaces"></a>Genel Arabirimler  
 Birlikte çalışma derlemesinden gömülü genel arabirimler kullanılamaz. Bu, aşağıdaki örnekte gösterilir.  
  
 [!code-vb[VbLinkCompiler#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/module1.vb#1)]  
  
### <a name="types-that-have-generic-parameters"></a>Genel parametrelere sahip türler  
 Türü bir birlikte çalışma derlemesinden gömülü olan genel bir parametreye sahip türler, bu tür bir dış derlemeden ise kullanılamaz. Bu kısıtlama, arabirimler için geçerlidir. Örneğin, <xref:Microsoft.Office.Interop.Excel.Range> <xref:Microsoft.Office.Interop.Excel> derlemede tanımlanan arabirimi göz önünde bulundurun. Bir kitaplık, <xref:Microsoft.Office.Interop.Excel> birlikte çalışma türlerini derlemeden katıştırır ve türü <xref:Microsoft.Office.Interop.Excel.Range> arabirim olan bir parametreye sahip genel bir tür döndüren bir yöntemi ortaya koyar, bu yöntem, aşağıdaki kod örneğinde gösterildiği gibi genel bir arabirim döndürmelidir.  
  
 [!code-vb[VbLinkCompiler#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/utility.vb#2)]  
[!code-vb[VbLinkCompiler#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/utility.vb#3)]  
[!code-vb[VbLinkCompiler#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/utility.vb#4)]  
  
 Aşağıdaki örnekte, istemci kodu hata olmadan <xref:System.Collections.IList> genel arabirimi döndüren yöntemi çağırabilir.  
  
 [!code-vb[VbLinkCompiler#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/module1.vb#5)]  
  
## <a name="example"></a>Örnek  
 `OfficeApp.vb` Aşağıdaki komut satırı, `COMData1.dll` ve `COMData2.dll` için `OfficeApp.exe`kaynak dosya ve başvuru derlemelerini derler.  
  
```console  
vbc -link:COMData1.dll,COMData2.dll /out:OfficeApp.exe OfficeApp.vb  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [İzlenecek yol: Yönetilen derlemelerden tür ekleme](../../../visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-vs.md)
- [-başvuru (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
- [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [-libpath](../../../visual-basic/reference/command-line-compiler/libpath.md)
- [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [COM Birlikte Çalışma'ya Giriş](../../../visual-basic/programming-guide/com-interop/introduction-to-com-interop.md)
