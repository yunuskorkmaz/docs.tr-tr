---
title: 'Nasıl yapılır: Bir derlemeyi güçlü bir adla imzala'
ms.date: 08/20/2019
helpviewer_keywords:
- strong-named assemblies, signing with strong names
- signing assemblies
- assemblies [.NET Framework], signing
- assemblies [.NET Framework], strong-named
ms.assetid: 2c30799a-a826-46b4-a25d-c584027a6c67
author: rpetrusha
ms.author: ronpet
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 527fd68ef40e152b57a1fc98113094d3b41fbaae
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70973063"
---
# <a name="how-to-sign-an-assembly-with-a-strong-name"></a>Nasıl yapılır: Bir derlemeyi güçlü bir adla imzala

> [!NOTE]
> .NET Core, tanımlayıcı adlı derlemeleri desteklese de, .NET Core kitaplığındaki tüm derlemeler imzalansa da, üçüncü taraf derlemelerin çoğunluğunun tanımlayıcı adlara ihtiyacı yoktur. Daha fazla bilgi için bkz. GitHub 'da [tanımlayıcı ad imzalama](https://github.com/dotnet/corefx/blob/master/Documentation/project-docs/strong-name-signing.md) .

Bir derlemeyi katı bir adla imzalamak için çeşitli yollar vardır:  
  
- Visual Studio 'da bir projenin **Özellikler** Iletişim kutusunda **imzalama** sekmesini kullanarak. Bu, bir derlemeyi katı bir adla imzalamanın en kolay ve en kullanışlı yoludur.  
  
- Bir .NET Framework kodu modülünü ( *. netmodule* dosyası) anahtar dosyasıyla bağlamak Için [derleme Bağlayıcısı (al. exe)](../../framework/tools/al-exe-assembly-linker.md) kullanarak.  
  
- Katı ad bilgilerini kodunuza eklemek için derleme özniteliklerini kullanarak. Kullanılacak anahtar dosyasının bulunduğu yere <xref:System.Reflection.AssemblyKeyFileAttribute> bağlı olarak <xref:System.Reflection.AssemblyKeyNameAttribute> ya da özniteliğini kullanabilirsiniz.  
  
- Derleyici seçeneklerini kullanarak.  
  
 Bir derlemeye katı bir ad atamak için bir şifreleme anahtarı çiftiniz olması gerekir. Anahtar çifti oluşturma hakkında daha fazla bilgi için bkz [. nasıl yapılır: Ortak özel anahtar çifti](create-public-private-key-pair.md)oluşturun.  
  
## <a name="create-and-sign-an-assembly-with-a-strong-name-by-using-visual-studio"></a>Visual Studio 'Yu kullanarak tanımlayıcı ad ile derleme oluşturma ve imzalama  
  
1. **Çözüm Gezgini**' de, proje için kısayol menüsünü açın ve ardından **Özellikler**' i seçin.  
  
2. **İmzalama** sekmesini seçin.  
  
3. **Derlemeyi imzala** kutusunu seçin.  
  
4. **Tanımlayıcı ad seçin anahtar dosyası** kutusunda, **Araştır**' ı seçin ve ardından anahtar dosyasına gidin. Yeni bir anahtar dosyası oluşturmak için **Yeni** ' yi seçin ve **tanımlayıcı ad anahtarı oluştur** iletişim kutusuna adını girin.  
  
> [!NOTE]
> [Bir derlemeyi imzalamayı geciktirmek](delay-sign.md)için bir ortak anahtar dosyası seçin.  
  
### <a name="create-and-sign-an-assembly-with-a-strong-name-by-using-the-assembly-linker"></a>Derleme bağlayıcı kullanarak tanımlayıcı ad ile derleme oluşturma ve imzalama  
  
[Visual Studio için geliştirici komut istemi](../../framework/tools/developer-command-prompt-for-vs.md), aşağıdaki komutu girin:  

**Al** **/Out:** \<AssemblyNameModuleName> > **/keyfile**:keyfilename\< *\<* >  

Konum:  

- *AssemblyName* , derleme bağlayıcının Yayladığı, kesin imzalı derlemenin (bir *. dll* veya *. exe* dosyası) adıdır.  
  
- *ModuleName* bir veya daha fazla tür içeren bir .NET Framework kod modülünün ( *. netmodule* dosyası) adıdır. Kodunuzu`/target:module` veya Visual Basic içindeki C# anahtarla derleyerek bir *. netmodule* dosyası oluşturabilirsiniz.
  
- *Keyfilename* , anahtar çiftini içeren kapsayıcının veya dosyanın adıdır. Derleme Bağlayıcı, geçerli dizinle ilişkili bir göreli yolu yorumlar.  

Aşağıdaki örnek, *sgKey. snk*anahtar dosyasını kullanarak *MyAssembly. dll* derlemesini tanımlayıcı bir adla imzalar.  

```console
al /out:MyAssembly.dll MyModule.netmodule /keyfile:sgKey.snk  
```  
  
Bu araç hakkında daha fazla bilgi için bkz. [derleme Bağlayıcısı](../../framework/tools/al-exe-assembly-linker.md).  
  
## <a name="sign-an-assembly-with-a-strong-name-by-using-attributes"></a>Öznitelikleri kullanarak bir derlemeyi tanımlayıcı adla imzalama  
  
1. Kaynak kodu dosyanıza <xref:System.Reflection.AssemblyKeyNameAttribute>orözniteliğini ekleyin ve derlemeyi tanımlayıcı bir adla imzalarken kullanılacak anahtar çiftini içeren dosya veya kapsayıcının adını belirtin. <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=nameWithType>  
   
2. Kaynak kodu normal şekilde derleyin.  
   
   > [!NOTE]
   > C# Ve Visual Basic derleyicileri, kaynak kodundaki <xref:System.Reflection.AssemblyKeyFileAttribute> veya <xref:System.Reflection.AssemblyKeyNameAttribute> özniteliğiyle karşılaştığında derleyici uyarılarını (sırasıyla CS1699 ve BC41008) yayınlarlar. Uyarıları gözardı edebilirsiniz.  

Aşağıdaki örnek <xref:System.Reflection.AssemblyKeyFileAttribute> özniteliğini, derlemenin derlendiği dizinde bulunan *keyfile. snk*adlı anahtar dosyasıyla birlikte kullanır.  

```cpp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")];
```

```csharp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")]
```

```vb
<Assembly:AssemblyKeyFileAttribute("keyfile.snk")>
```

Ayrıca kaynak dosyanızı derlerken bir derlemeyi imzalamayı erteleyebilirsiniz. Daha fazla bilgi için bkz. [bir derlemeyi Gecikmeli imzalama](delay-sign.md).  

## <a name="sign-an-assembly-with-a-strong-name-by-using-the-compiler"></a>Derleyici kullanarak bir derlemeyi tanımlayıcı adla imzalama  

Kaynak `/keyfile` kodu dosyanızı veya dosyalarınızı, veya Visual Basic içindeki C# or `/delaysign` derleyici seçeneğiyle veya `/KEYFILE` ' de `/DELAYSIGN` C++veya bağlayıcı seçeneğinde derleyin. Seçenek adından sonra, iki nokta işareti ve anahtar dosyasının adını ekleyin. Komut satırı derleyicileri kullanırken, anahtar dosyasını kaynak kodu dosyalarınızı içeren dizine kopyalayabilirsiniz.  

Gecikmeli imzalama hakkında daha fazla bilgi için bkz. [bir derlemeyi gecikmeli](delay-sign.md)imzalama.  

Aşağıdaki örnek, C# derleyicisini kullanır ve *bir derlemeyi,* *sgKey. snk*anahtar dosyasını kullanarak tanımlayıcı bir adla imzalar.  

```cmd
csc /t:library UtilityLibrary.cs /keyfile:sgKey.snk  
```  

## <a name="see-also"></a>Ayrıca bkz.

- [Tanımlayıcı adlı derlemeler oluşturma ve kullanma](create-use-strong-named.md)
- [Nasıl yapılır: Ortak özel anahtar çifti oluşturma](create-public-private-key-pair.md)
- [Al.exe (Bütünleştirilmiş Kod Bağlayıcı)](../../framework/tools/al-exe-assembly-linker.md)
- [Bir derlemeyi gecikmeli imzala](delay-sign.md)
- [Derleme ve bildirim imzalamayı yönetme](/visualstudio/ide/managing-assembly-and-manifest-signing)
- [İmzalama sayfası, proje Tasarımcısı](/visualstudio/ide/reference/signing-page-project-designer)
