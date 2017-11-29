---
title: "-bağlantı (C# Derleyici Seçenekleri)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
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
caps.latest.revision: "13"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 229bd7e6a7f3691bcb4e6c6dab6f9f36dc3d45f5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="link-c-compiler-options"></a>/link (C# Derleyici Seçenekleri)
Derleyici COM türü bilgileri belirtilen derlemelerde şu anda derlediğiniz proje kullanılabilir hale getirmek neden olur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
/link:fileList  
// -or-  
/l:fileList  
```  
  
## <a name="arguments"></a>Arguments  
 `fileList`  
 Gerekli. Derleme dosya adlarının virgülle ayrılmış listesi. Dosya adı boşluk içeriyorsa adı tırnak işaretleri içine alın.  
  
## <a name="remarks"></a>Açıklamalar  
 `/link` Seçeneği katıştırılmış türde bilgi içeren bir uygulama dağıtmanıza olanak sağlar. Uygulamanın gömülü tür bilgileri çalışma zamanı derlemesine başvuru gerek kalmadan uygulama çalışma zamanı derlemesi türlerinde sonra kullanabilirsiniz. Çeşitli çalışma zamanı derleme sürümleri yayımladıysanız katıştırılmış tür bilgileri içeren uygulama derlenmesi gerek kalmadan çeşitli sürümleriyle çalışabilir. Bir örnek için bkz: [izlenecek yol: yönetilen derlemelerden türler katıştırma](../../programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md).  
  
 Kullanarak `/link` COM birlikte çalışma ile çalışırken seçenek özellikle yararlıdır. Böylelikle, uygulamanızın artık hedef bilgisayarda birincil birlikte çalışma derlemesi (PIA) gerektirir COM türlerini eklenebilir. `/link` Seçeneği elde edilen derlenmiş kod başvurulan birlikte çalışma derlemeye COM tür bilgilerini katıştırma derleyici bildirir. COM türü CLSID (GUID) değeri tarafından tanımlanır. Sonuç olarak, uygulamanızı aynı CLSID değerlerine sahip aynı COM türlerini yüklü olduğu bir hedef bilgisayarda çalıştırabilirsiniz. Microsoft Office'i otomatikleştiren uygulamalar iyi bir örnektir. Office gibi uygulamalar genellikle farklı sürümleri arasında aynı CLSID değeri tutmak için uygulamanız başvurulan COM türlerini uzun .NET Framework 4 veya daha sonra hedef bilgisayarda yüklü olduğundan ve yöntemler, özellikler, uygulamanızın kullandığı gibi kullanabilirsiniz veya Başvurulan COM türlerinde dahil olaylar.  
  
 `/link` Seçeneği yalnızca arabirimleri, yapılar ve temsilciler katıştırır. COM sınıfları katıştırma desteklenmiyor.  
  
> [!NOTE]
>  Kodunuzda katıştırılmış COM türünün bir örneğini oluştururken uygun arabirimi kullanarak örneği oluşturmanız gerekir. Coclass'ı kullanarak katıştırılmış COM türünün bir örneği oluşturulmaya çalışılırken bir hata neden olur.  
  
 Ayarlamak için `/link` seçeneğini [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)], bir derleme başvurusu ekleyin ve ayarlayın `Embed Interop Types` özelliğine **doğru**. İçin varsayılan `Embed Interop Types` özelliği **false**.  
  
 Bir COM derlemesine (a derlemesi) bağlantısının kendisi başka bir COM derlemesine (derleme B) başvuruyor, aşağıdakilerden biri doğruysa B derlemesine bağlantı gerekir:  
  
-   Derlemesi türünden bir türden devralır veya derleme B'deki bir arabirimi uygular.  
  
-   Alan, özellik, olay veya b derlemesinden dönüş türü veya parametresi türü olan yöntemi çağrılır.  
  
 Gibi [/reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md) derleyici seçeneği `/link` derleyici seçeneği başvuruları sık kullanılan Csc.rsp yanıt dosyası kullanan [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] derlemeler. Kullanmak [/noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md) derleyicinin Csc.rsp dosyasını kullanmasını istemiyorsanız derleyici seçeneği.  
  
 Kısa formunu `/link` olan `/l`.  
  
## <a name="generics-and-embedded-types"></a>Genel türler ve katıştırılmış türler  
 Aşağıdaki bölümlerde, genel türler birlikte çalışma türlerini katıştır uygulamalarında kullanma sınırlamaları açıklanmaktadır.  
  
### <a name="generic-interfaces"></a>Genel Arabirimler  
 Birlikte çalışma bir derlemeden katıştırılmış genel arabirimler kullanılamaz. Bu, aşağıdaki örnekte gösterilir.  
  
 [!code-csharp[VbLinkCompilerCS#1](../../../csharp/language-reference/compiler-options/codesnippet/CSharp/link-compiler-option_1.cs)]  
  
### <a name="types-that-have-generic-parameters"></a>Genel Parametreler türleri  
 Türü birlikte çalışma bir derlemeden katıştırılmış genel bir parametre türleri, dış bir derlemeden tür olan kullanılamaz. Bu kısıtlama, arabirimler için geçerli değil. Örneğin, göz önünde bulundurun <xref:Microsoft.Office.Interop.Excel.Range> tanımlanan arabirimi <xref:Microsoft.Office.Interop.Excel> derleme. Birlikte çalışma türlerini kitaplık katıştırır, <xref:Microsoft.Office.Interop.Excel> derleme ve bir parametreye sahip genel bir tür, türü döndüren bir yöntem sunarsa <xref:Microsoft.Office.Interop.Excel.Range> arabirim, yöntem aşağıdaki kod örneğinde gösterildiği gibi genel bir arabirim döndürmelidir.  
  
 [!code-csharp[VbLinkCompilerCS#2](../../../csharp/language-reference/compiler-options/codesnippet/CSharp/link-compiler-option_2.cs)]  
[!code-csharp[VbLinkCompilerCS#3](../../../csharp/language-reference/compiler-options/codesnippet/CSharp/link-compiler-option_3.cs)]  
[!code-csharp[VbLinkCompilerCS#4](../../../csharp/language-reference/compiler-options/codesnippet/CSharp/link-compiler-option_4.cs)]  
  
 Aşağıdaki örnekte, istemci kodu döndürür yöntemini çağırabilir <xref:System.Collections.IList> hatasız genel arabirim.  
  
 [!code-csharp[VbLinkCompilerCS#5](../../../csharp/language-reference/compiler-options/codesnippet/CSharp/link-compiler-option_5.cs)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod kaynak dosyasını derler `OfficeApp.cs` ve başvuru derlemelerden `COMData1.dll` ve `COMData2.dll` üretmek için `OfficeApp.exe`.  
  
```csharp  
csc /link:COMData1.dll,COMData2.dll /out:OfficeApp.exe OfficeApp.cs  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)  
 [İzlenecek yol: Yönetilen derlemelerden türler katıştırma](../../programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md)  
 [/ Reference (C# Derleyici Seçenekleri)](../../../csharp/language-reference/compiler-options/reference-compiler-option.md)  
 [/ noconfig (C# Derleyici Seçenekleri)](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md)  
 [Komut satırı csc.exe derleme](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)  
 [Birlikte çalışabilirliğe genel bakış](../../../csharp/programming-guide/interop/interoperability-overview.md)
