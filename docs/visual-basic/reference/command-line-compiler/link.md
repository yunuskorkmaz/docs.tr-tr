---
title: -link
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
ms.openlocfilehash: 3c02c914a27e6095f8f6bc34e29e2447a1a373e5
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91065729"
---
# <a name="-link-visual-basic"></a>-bağlantı (Visual Basic)

Derleyicinin, belirtilen derlemelerdeki COM tür bilgilerini şu anda derlediğiniz projede kullanılabilir hale getirmesine neden olur.  
  
## <a name="syntax"></a>Syntax  
  
```console  
-link:fileList  
```

veya  

```console
-l:fileList  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  
  
|Terim|Tanım|  
|---|---|  
|`fileList`|Gereklidir. Bütünleştirilmiş kod dosyası adlarının virgülle ayrılmış listesi. Dosya adı bir boşluk içeriyorsa, adı tırnak işaretleri içine alın.|  
  
## <a name="remarks"></a>Açıklamalar  

 `-link`Seçeneği, gömülü tür bilgilerine sahip bir uygulamayı dağıtmanıza olanak sağlar. Uygulama daha sonra, çalışma zamanı derlemesine bir başvuruya gerek duymadan gömülü tür bilgilerini uygulayan bir çalışma zamanı derlemesinde türleri kullanabilir. Çalışma zamanı derlemesinin çeşitli sürümleri yayımlanıyorsa, katıştırılmış tür bilgilerini içeren uygulama, yeniden derlenmesi gerekmeden çeşitli sürümlerle çalışabilir. Bir örnek için bkz. [Izlenecek yol: yönetilen derlemelerden tür ekleme](../../../standard/assembly/embed-types-visual-studio.md).  
  
 Seçeneğinin kullanılması `-link` özellıkle com birlikte çalışabilirliğine çalışırken yararlıdır. Uygulamanızın artık hedef bilgisayarda bir birincil birlikte çalışma derlemesi (PIA) gerektirmemesi için COM türlerini katıştırabilirsiniz. `-link`Seçeneği, derleyicinin başvurulan birlikte çalışma DERLEMESINDEKI com tür bilgilerini sonuçta elde edilen derlenmiş koda katıştırmasını söyler. COM türü, CLSID (GUID) değeri tarafından tanımlanır. Sonuç olarak, uygulamanız aynı CLSID değerleriyle aynı COM türlerini yükleyen bir hedef bilgisayarda çalışabilir. Microsoft Office otomatikleştiren uygulamalar iyi bir örnektir. Office gibi uygulamalar genellikle farklı sürümlerde aynı CLSID değerini tutacağından, uygulamanız başvurulan COM türlerini, .NET Framework 4 veya üzeri hedef bilgisayara yüklendiği sürece ve uygulamanız başvurulan COM türlerine dahil olan yöntemleri, özellikleri veya olayları kullandığında kullanabilirsiniz.  
  
 `-link`Seçeneği yalnızca arabirimleri, yapıları ve temsilcileri katıştırır. COM sınıfları ekleme desteklenmiyor.  
  
> [!NOTE]
> Kodunuzda gömülü bir COM türünün örneğini oluşturduğunuzda, uygun arabirimi kullanarak örneği oluşturmanız gerekir. CoClass kullanarak gömülü COM türünün bir örneğini oluşturma girişimi hataya neden olur.  
  
 `-link`Visual Studio 'da seçeneğini ayarlamak için bir derleme başvurusu ekleyin ve `Embed Interop Types` özelliği **true**olarak ayarlayın. Özelliği için varsayılan değer `Embed Interop Types` **false**'dur.  
  
 Başka bir COM derlemesine (derleme B) başvuran bir COM derlemesine (derleme A) bağlarsanız, aşağıdakilerden biri doğruysa derleme B 'ye de bağlantı oluşturmanız gerekir:  
  
- Derleme A 'dan bir tür bir türden devralınır veya derleme B 'den bir arabirim uygular.  
  
- B derlemesinden dönüş türü veya parametre türü olan bir alan, özellik, olay veya yöntem çağrılır.  
  
 Bir veya daha fazla derleme başvurularınızın bulunduğu dizini belirtmek için [-libpath](libpath.md) kullanın.  
  
 [-Reference](reference.md) derleyici seçeneği gibi, `-link` derleyici seçeneği de sık kullanılan .NET Framework derlemelerine başvuran Vbc. rsp yanıt dosyasını kullanır. Derleyicinin Vbc. rsp dosyasını kullanmasını istemiyorsanız [-noconfig](noconfig.md) derleyici seçeneğini kullanın.  
  
 Öğesinin kısa biçimi `-link` `-l` .  
  
## <a name="generics-and-embedded-types"></a>Genel türler ve katıştırılmış türler  

 Aşağıdaki bölümlerde, birlikte çalışma türlerini gömün uygulamalarda genel türleri kullanma sınırlamaları açıklanır.  
  
### <a name="generic-interfaces"></a>Genel Arabirimler  

 Birlikte çalışma derlemesinden gömülü genel arabirimler kullanılamaz. Bu, aşağıdaki örnekte gösterilir.  
  
 [!code-vb[VbLinkCompiler#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/module1.vb#1)]  
  
### <a name="types-that-have-generic-parameters"></a>Genel parametrelere sahip türler  

 Türü bir birlikte çalışma derlemesinden gömülü olan genel bir parametreye sahip türler, bu tür bir dış derlemeden ise kullanılamaz. Bu kısıtlama, arabirimler için geçerlidir. Örneğin, <xref:Microsoft.Office.Interop.Excel.Range> derlemede tanımlanan arabirimi göz önünde bulundurun <xref:Microsoft.Office.Interop.Excel> . Bir kitaplık, birlikte çalışma türlerini derlemeden katıştırır <xref:Microsoft.Office.Interop.Excel> ve türü arabirim olan bir parametreye sahip genel bir tür döndüren bir yöntemi ortaya koyar <xref:Microsoft.Office.Interop.Excel.Range> , bu yöntem, aşağıdaki kod örneğinde gösterildiği gibi genel bir arabirim döndürmelidir.  
  
 [!code-vb[VbLinkCompiler#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/utility.vb#2)]  
[!code-vb[VbLinkCompiler#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/utility.vb#3)]  
[!code-vb[VbLinkCompiler#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/utility.vb#4)]  
  
 Aşağıdaki örnekte, istemci kodu <xref:System.Collections.IList> hata olmadan genel arabirimi döndüren yöntemi çağırabilir.  
  
 [!code-vb[VbLinkCompiler#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/module1.vb#5)]  
  
## <a name="example"></a>Örnek  

 Aşağıdaki komut satırı, `OfficeApp.vb` ve için kaynak dosya ve başvuru derlemelerini `COMData1.dll` derler `COMData2.dll` `OfficeApp.exe` .  
  
```console  
vbc -link:COMData1.dll,COMData2.dll -out:OfficeApp.exe OfficeApp.vb  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](index.md)
- [İzlenecek yol: Yönetilen Bütünleştirilmiş Kodlardan Türler Katıştırma](../../../standard/assembly/embed-types-visual-studio.md)
- [-başvuru (Visual Basic)](reference.md)
- [-noconfig](noconfig.md)
- [-libpath](libpath.md)
- [Örnek Derleme Komut Satırları](sample-compilation-command-lines.md)
- [COM Birlikte Çalışma'ya Giriş](../../programming-guide/com-interop/introduction-to-com-interop.md)
