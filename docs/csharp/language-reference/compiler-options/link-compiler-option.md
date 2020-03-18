---
title: -link (C# Derleyici Seçenekleri)
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
ms.openlocfilehash: 4c96f7be5ac500886ea036c93b4651fa814ee58a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70970104"
---
# <a name="-link-c-compiler-options"></a>-link (C# Derleyici Seçenekleri)
Derleyicinin, şu anda derlemekte olduğunuz projeiçin belirtilen derlemelerde COM türü bilgilerini kullanılabilir hale getirmelerine neden olur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-link:fileList  
// -or-  
-l:fileList  
```  
  
## <a name="arguments"></a>Bağımsız Değişkenler  
 `fileList`  
 Gereklidir. Derleme dosya adlarının virgülle sınırlandırıladaki listesi. Dosya adı bir boşluk içeriyorsa, adı tırnak işaretlerine ekin.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu `-link` seçenek, tür bilgilerini katıştüre eden bir uygulama dağıtmanızı sağlar. Uygulama daha sonra, çalışma zamanı derlemesine başvuru gerektirmeden katıştırılmış tür bilgilerini uygulayan çalışma zamanı derlemesi türlerini kullanabilir. Çalışma zamanı derlemesinin çeşitli sürümleri yayımlanırsa, katıştılı tür bilgilerini içeren uygulama yeniden derlenmek zorunda kalmadan çeşitli sürümlerle çalışabilir. Örneğin, [Bkz. Walkthrough: Yönetilen Derlemelerden Türleri Katıştırma.](../../../standard/assembly/embed-types-visual-studio.md)  
  
 `-link` Seçeneği kullanmak özellikle COM interop ile çalışırken kullanışlıdır. Com türlerini, uygulamanızın artık hedef bilgisayara birincil interop derlemesi (PIA) gerektirmeyin diye katıştırabilirsiniz. Seçenek, `-link` derleyiciye, başvurulan interop derlemesinden COM türü bilgilerini elde edilen derlenmiş koda gömmesini bildirir. COM türü CLSID (GUID) değeri ile tanımlanır. Sonuç olarak, uygulamanız aynı CLSID değerlerine sahip aynı COM türlerini yüklemiş bir hedef bilgisayarda çalıştırılabilir. Microsoft Office'i otomatikleştiren uygulamalar iyi bir örnektir. Office gibi uygulamalar genellikle farklı sürümler arasında aynı CLSID değerini tuttuğundan, başvurulan COM türlerini hedef bilgisayara .NET Framework 4 veya sonraki olarak yüklenmiş ve uygulamanız yöntemleri, özellikleri veya başvurulan COM türlerine dahil olan olaylar.  
  
 Seçenek `-link` yalnızca arabirimleri, yapıları ve temsilcileri katıştırıyor. Gömme COM sınıfları desteklenmez.  
  
> [!NOTE]
> Kodunuzda gömülü bir COM türü örneği oluşturduğunuzda, uygun arabirimi kullanarak örneği oluşturmanız gerekir. CoClass kullanarak katıştırılmış com türü bir örnek oluşturmaya çalışırken bir hataya neden olur.  
  
 Visual Studio'da `-link` seçeneği ayarlamak için bir montaj `Embed Interop Types` başvurusu ekleyin ve özelliği **doğru**olarak ayarlayın. `Embed Interop Types` Özellik için varsayılan **yanlıştır.**  
  
 Başka bir COM derlemesine (B Derlemesi) atıfta bulunan bir COM derlemesine (A Derlemesi) bağlantı verirseniz, aşağıdakilerden biri doğruysa B Derlemesi'ne de bağlanmanız gerekir:  
  
- A Derlemesi'nden bir tür bir türdevralır veya B Derlemesi'nden bir arabirim uygular.  
  
- B derlemesinden iade türü veya parametre türü olan bir alan, özellik, olay veya yöntem çağrılır.  
  
 [-başvuru](./reference-compiler-option.md) derleyici seçeneği gibi, `-link` derleyici seçeneği de sık sık kullanılan .NET Framework derlemelerine başvuran Csc.rsp yanıt dosyasını kullanır. Derleyicinin Csc.rsp dosyasını kullanmasını istemiyorsanız [-noconfig](./noconfig-compiler-option.md) derleyici seçeneğini kullanın.  
  
 Kısa formu `-link` `-l`.  
  
## <a name="generics-and-embedded-types"></a>Genel ler ve Gömülü Türler  
 Aşağıdaki bölümlerde interop türleri katıştırma uygulamalarında genel türleri kullanarak sınırlamaları açıklayınız.  
  
### <a name="generic-interfaces"></a>Genel Arabirimler  
 Interop derlemesinden katıştürilmiş genel arabirimler kullanılamaz. Bu, aşağıdaki örnekte gösterilir.  
  
 [!code-csharp[VbLinkCompilerCS#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vblinkcompilercs/cs/program.cs#1)]  
  
### <a name="types-that-have-generic-parameters"></a>Genel Parametrelere Sahip Türler  
 Bu tür harici bir derlemeden geliyorsa, türü bir interop derlemesinden katıştırılmış genel bir parametreye sahip türler kullanılamaz. Bu kısıtlama arabirimler için geçerli değildir. Örneğin, <xref:Microsoft.Office.Interop.Excel> derlemede <xref:Microsoft.Office.Interop.Excel.Range> tanımlanan arabirimi göz önünde bulundurun. Kitaplık derlemeden interop türlerini <xref:Microsoft.Office.Interop.Excel> katıştırır ve türü <xref:Microsoft.Office.Interop.Excel.Range> arabirim olan bir parametreye sahip genel bir türdöndüren bir yöntem ortaya çıkarırsa, bu yöntemin aşağıdaki kod örneğinde gösterildiği gibi genel bir arabirim döndürmesi gerekir.  
  
 [!code-csharp[VbLinkCompilerCS#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vblinkcompilercs/cs/utility.cs#2)]  
[!code-csharp[VbLinkCompilerCS#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vblinkcompilercs/cs/utility.cs#3)]  
[!code-csharp[VbLinkCompilerCS#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vblinkcompilercs/cs/utility.cs#4)]  
  
 Aşağıdaki örnekte, istemci kodu <xref:System.Collections.IList> genel arabirimi hatasız döndüren yöntemi çağırabilir.  
  
 [!code-csharp[VbLinkCompilerCS#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vblinkcompilercs/cs/program.cs#5)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod kaynak dosya `OfficeApp.cs` ve başvuru `COMData1.dll` derlemeleri derler ve `COMData2.dll` üretmek `OfficeApp.exe`için.  
  
```csharp  
csc -link:COMData1.dll,COMData2.dll -out:OfficeApp.exe OfficeApp.cs  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](./index.md)
- [İzlenecek yol: Yönetilen Bütünleştirilmiş Kodlardan Türler Katıştırma](../../../standard/assembly/embed-types-visual-studio.md)
- [-referans (C# Derleyici Seçenekleri)](./reference-compiler-option.md)
- [-noconfig (C# Derleyici Seçenekleri)](./noconfig-compiler-option.md)
- [csc.exe Kullanarak Komut Satırı Derleme](./command-line-building-with-csc-exe.md)
- [Birlikte Çalışabilirliğe Genel Bakış](../../programming-guide/interop/interoperability-overview.md)
