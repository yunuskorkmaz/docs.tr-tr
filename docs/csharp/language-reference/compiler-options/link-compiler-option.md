---
description: -Link (C# derleyici seçenekleri)
title: -Link (C# derleyici seçenekleri)
ms.date: 07/20/2015
helpviewer_keywords:
- /l compiler option [C#]
- /link compiler option [C#]
- -l compiler option [C#]
- EmbedInteropTypes
- l compiler option [C#]
- embed interop types [COM Interop]
- -link compiler option [C#]
- link compiler option [C#]
ms.assetid: 00da70c6-9ea1-43c2-86f2-aa7f26c03475
ms.openlocfilehash: 6fd291c49c282713ea56ca20d8d58616d38ec752
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2020
ms.locfileid: "89465721"
---
# <a name="-link-c-compiler-options"></a>-Link (C# derleyici seçenekleri)
Derleyicinin, belirtilen derlemelerdeki COM tür bilgilerini şu anda derlediğiniz projede kullanılabilir hale getirmesine neden olur.

## <a name="syntax"></a>Söz dizimi

```console
-link:fileList
// -or-
-l:fileList
```

## <a name="arguments"></a>Bağımsız değişkenler
 `fileList`  
 Gereklidir. Bütünleştirilmiş kod dosyası adlarının virgülle ayrılmış listesi. Dosya adı bir boşluk içeriyorsa, adı tırnak işaretleri içine alın.

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

 [-Reference](./reference-compiler-option.md) derleyici seçeneği gibi, `-link` derleyici seçeneği sık kullanılan .NET derlemelerine başvuran Csc. rsp yanıt dosyasını kullanır. Derleyicinin Csc. rsp dosyasını kullanmasını istemiyorsanız [-noconfig](./noconfig-compiler-option.md) derleyici seçeneğini kullanın.

 Öğesinin kısa biçimi `-link` `-l` .

## <a name="generics-and-embedded-types"></a>Genel türler ve katıştırılmış türler
 Aşağıdaki bölümlerde, birlikte çalışma türlerini gömün uygulamalarda genel türleri kullanma sınırlamaları açıklanır.

### <a name="generic-interfaces"></a>Genel Arabirimler
 Birlikte çalışma derlemesinden gömülü genel arabirimler kullanılamaz. Bu, aşağıdaki örnekte gösterilir.

 [!code-csharp[VbLinkCompilerCS#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vblinkcompilercs/cs/program.cs#1)]

### <a name="types-that-have-generic-parameters"></a>Genel parametrelere sahip türler
 Türü bir birlikte çalışma derlemesinden gömülü olan genel bir parametreye sahip türler, bu tür bir dış derlemeden ise kullanılamaz. Bu kısıtlama, arabirimler için geçerlidir. Örneğin, <xref:Microsoft.Office.Interop.Excel.Range> derlemede tanımlanan arabirimi göz önünde bulundurun <xref:Microsoft.Office.Interop.Excel> . Bir kitaplık, birlikte çalışma türlerini derlemeden katıştırır <xref:Microsoft.Office.Interop.Excel> ve türü arabirim olan bir parametreye sahip genel bir tür döndüren bir yöntemi ortaya koyar <xref:Microsoft.Office.Interop.Excel.Range> , bu yöntem, aşağıdaki kod örneğinde gösterildiği gibi genel bir arabirim döndürmelidir.

[!code-csharp[VbLinkCompilerCS#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vblinkcompilercs/cs/utility.cs)]

 Aşağıdaki örnekte, istemci kodu <xref:System.Collections.IList> hata olmadan genel arabirimi döndüren yöntemi çağırabilir.

 [!code-csharp[VbLinkCompilerCS#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vblinkcompilercs/cs/program.cs#5)]

## <a name="example"></a>Örnek
 Aşağıdaki kod, `OfficeApp.cs` ve için kaynak dosyası ve başvuru derlemelerini `COMData1.dll` derler `COMData2.dll` `OfficeApp.exe` .

```csharp
csc -link:COMData1.dll,COMData2.dll -out:OfficeApp.exe OfficeApp.cs
```

## <a name="see-also"></a>Ayrıca bkz.

- [C# derleyici seçenekleri](./index.md)
- [İzlenecek yol: Yönetilen Bütünleştirilmiş Kodlardan Türler Katıştırma](../../../standard/assembly/embed-types-visual-studio.md)
- [-Reference (C# derleyici seçenekleri)](./reference-compiler-option.md)
- [-noconfig (C# derleyici seçenekleri)](./noconfig-compiler-option.md)
- [csc.exe Kullanarak Komut Satırı Derleme](./command-line-building-with-csc-exe.md)
- [Birlikte Çalışabilirliğe Genel Bakış](../../programming-guide/interop/interoperability-overview.md)
