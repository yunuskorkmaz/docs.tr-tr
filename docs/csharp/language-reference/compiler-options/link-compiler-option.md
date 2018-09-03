---
title: -bağlantı (C# Derleyici Seçenekleri)
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
ms.openlocfilehash: 00cfda489feb468c7e3c140ab63369b408b09152
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43484458"
---
# <a name="-link-c-compiler-options"></a>-bağlantı (C# Derleyici Seçenekleri)
Derleyici COM tür bilgilerini belirli derlemelerde şu anda derleme proje kullanılabilir hale getirmek neden olur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-link:fileList  
// -or-  
-l:fileList  
```  
  
## <a name="arguments"></a>Arguments  
 `fileList`  
 Gerekli. Derleme dosya adlarının virgülle ayrılmış liste. Dosya adı boşluk içeriyorsa adı tırnak içine alın.  
  
## <a name="remarks"></a>Açıklamalar  
 `-link` Seçeneği, gömülü tür bilgileri içeren bir uygulama dağıtmanıza olanak sağlar. Uygulama, daha sonra bir çalışma zamanı derlemesindeki gömülü tür bilgileri, çalışma zamanı derlemeye bir başvuruda gerek kalmadan uygulayan türler kullanabilirsiniz. Çeşitli çalışma zamanı derleme sürümleri yayımladıysanız, gömülü tür bilgileri içeren uygulama derlenmesi gerek kalmadan çeşitli sürümleriyle çalışabilir. Bir örnek için bkz. [izlenecek yol: yönetilen derlemelerden türler katıştırma](../../programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md).  
  
 Kullanarak `-link` COM birlikte çalışma ile çalışırken seçenek özellikle yararlıdır. Uygulamanız artık hedef bilgisayarda birincil birlikte çalışma derlemesi (PIA) gerektirmemesi için COM türlerini ekleyebilir. `-link` Başvurulan birlikte çalışma bütünleştirilmiş kod içine ortaya çıkan derlenmiş kodu COM tür bilgilerini katıştırma derleyici seçeneği bildirir. COM türü (GUID) CLSID değeri tarafından tanımlanır. Sonuç olarak, uygulamanızı aynı COM türlerini aynı CLSID değerlerle yüklü olduğu bir hedef bilgisayarda çalıştırabilirsiniz. Microsoft Office otomatikleştirmek uygulamaların iyi bir örnektir. Office gibi uygulamalarda, genellikle aynı CLSID değeri farklı sürümler arasında tutmak olduğundan, uygulamanızı başvurulan COM türlerini uzun olarak .NET Framework 4 veya daha sonra hedef bilgisayarda yüklü olduğundan ve yöntemler, özellikler, uygulamanızın kullandığı gibi kullanabilirsiniz veya Başvurulan COM türlerini dahil edilen olaylar.  
  
 `-link` Seçeneği yalnızca arabirimleri, yapılar ve temsilciler ekler. COM sınıfları ekleme desteklenmiyor.  
  
> [!NOTE]
>  Kodunuzda katıştırılmış bir COM türün örneğini oluşturduğunuzda, uygun arabirimini kullanarak örneği oluşturmanız gerekir. Coclass'ı kullanarak katıştırılmış bir COM tür örneği oluşturulmaya çalışılırken bir hata oluşur.  
  
 Ayarlanacak `-link` seçeneğini Visual Studio'da ve bir bütünleştirilmiş kod Başvurusu Ekle `Embed Interop Types` özelliğini **true**. İçin varsayılan `Embed Interop Types` özelliği **false**.  
  
 Bir COM derlemesine (bütünleştirilmiş kod: A) bağlarsanız kendisi başka bir COM derlemesine (derleme B) başvuruda, aşağıdakilerden biri doğruysa, derleme B bağlamak de:  
  
-   Bir derlemeden bir tür bir tür tarafından devralındığında veya derleme B'deki bir arabirim uygular.  
  
-   Bir alan, özelliği, olay veya dönüş türü veya parametresi türü derleme b olan yöntemi çağrılır.  
  
 Gibi [-başvuru](../../../csharp/language-reference/compiler-options/reference-compiler-option.md) derleyici seçeneği `-link` derleyici seçeneği başvuru sık kullanılan Csc.rsp yanıt dosyası kullanan [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] derlemeler. Kullanma [- noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md) Csc.rsp dosyasını kullanmak için derleyicinin istemiyorsanız derleyici seçeneği.  
  
 Kısa formunu da `-link` olduğu `-l`.  
  
## <a name="generics-and-embedded-types"></a>Genel türler ve gömülü türleri  
 Aşağıdaki bölümlerde, genel türleri kullanarak birlikte çalışma türlerini katıştır uygulamalarda sınırlamaları açıklanmaktadır.  
  
### <a name="generic-interfaces"></a>Genel Arabirimler  
 Gömülü birlikte çalışma derlemesi genel arabirimler kullanılamaz. Bu, aşağıdaki örnekte gösterilir.  
  
 [!code-csharp[VbLinkCompilerCS#1](../../../csharp/language-reference/compiler-options/codesnippet/CSharp/link-compiler-option_1.cs)]  
  
### <a name="types-that-have-generic-parameters"></a>Genel parametre türleri  
 Genel parametre türü bir birlikte çalışma derlemesi katıştırılmış türleri, dış bütünleştirilmiş koddan tür olan kullanılamaz. Bu kısıtlama, arabirimler için geçerli değildir. Örneğin, düşünün <xref:Microsoft.Office.Interop.Excel.Range> tanımlanan arabirimi <xref:Microsoft.Office.Interop.Excel> derleme. Birlikte çalışma türleri bir kitaplığını katıştırır, <xref:Microsoft.Office.Interop.Excel> bütünleştirilmiş kod ve türü olan bir parametreye sahip genel bir tür döndüren bir yöntem sunarsa <xref:Microsoft.Office.Interop.Excel.Range> arabirim yöntemi aşağıdaki kod örneğinde gösterildiği gibi genel bir arabirim döndürmelidir.  
  
 [!code-csharp[VbLinkCompilerCS#2](../../../csharp/language-reference/compiler-options/codesnippet/CSharp/link-compiler-option_2.cs)]  
[!code-csharp[VbLinkCompilerCS#3](../../../csharp/language-reference/compiler-options/codesnippet/CSharp/link-compiler-option_3.cs)]  
[!code-csharp[VbLinkCompilerCS#4](../../../csharp/language-reference/compiler-options/codesnippet/CSharp/link-compiler-option_4.cs)]  
  
 Aşağıdaki örnekte, istemci kodu döndüren yöntem çağırabilirsiniz <xref:System.Collections.IList> hatasız genel arabirim.  
  
 [!code-csharp[VbLinkCompilerCS#5](../../../csharp/language-reference/compiler-options/codesnippet/CSharp/link-compiler-option_5.cs)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, kaynak dosyasını derler `OfficeApp.cs` ve başvuru derlemeleri `COMData1.dll` ve `COMData2.dll` üretmek için `OfficeApp.exe`.  
  
```csharp  
csc -link:COMData1.dll,COMData2.dll -out:OfficeApp.exe OfficeApp.cs  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)  
- [İzlenecek yol: Yönetilen Bütünleştirilmiş Kodlardan Türler Katıştırma](../../programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md)  
- [-başvurusu (C# Derleyici Seçenekleri)](../../../csharp/language-reference/compiler-options/reference-compiler-option.md)  
- [-noconfig (C# Derleyici Seçenekleri)](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md)  
- [csc.exe Kullanarak Komut Satırı Derleme](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)  
- [Birlikte Çalışabilirliğe Genel Bakış](../../../csharp/programming-guide/interop/interoperability-overview.md)
