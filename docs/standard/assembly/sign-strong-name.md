---
title: 'Nasıl yapilir: Güçlü bir ada sahip bir derlemeyi imzalama'
ms.date: 08/20/2019
helpviewer_keywords:
- strong-named assemblies, signing with strong names
- signing assemblies
- assemblies [.NET Framework], signing
- assemblies [.NET Framework], strong-named
ms.assetid: 2c30799a-a826-46b4-a25d-c584027a6c67
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 9998e69e8bf1505bcfc7a9103e9d89616dad9633
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160319"
---
# <a name="how-to-sign-an-assembly-with-a-strong-name"></a>Nasıl yapilir: Güçlü bir ada sahip bir derlemeyi imzalama

> [!NOTE]
> .NET Core güçlü adlandırılmış derlemeleri desteklese ve .NET Core kitaplığındaki tüm derlemeler imzalanmış olsa da, üçüncü taraf derlemelerin çoğunluğugüçlü adlara ihtiyaç duymaz. Daha fazla bilgi için GitHub'da [Güçlü Ad İmzalama'ya](https://github.com/dotnet/runtime/blob/master/docs/project/strong-name-signing.md) bakın.

Bir derlemeyi katı bir adla imzalamak için çeşitli yollar vardır:  
  
- Visual Studio'da projenin **Özellikler** iletişim kutusunda **İmzalama** sekmesini kullanarak. Bu, bir derlemeyi katı bir adla imzalamanın en kolay ve en kullanışlı yoludur.  
  
- Bir .NET Framework kod modüllerini *(.netmodule* dosyası) anahtar dosyasına bağlamak için [Derleme Bağlantı Cısı'nı (Al.exe)](../../framework/tools/al-exe-assembly-linker.md) kullanarak.  
  
- Katı ad bilgilerini kodunuza eklemek için derleme özniteliklerini kullanarak. Kullanılacak anahtar dosyasının <xref:System.Reflection.AssemblyKeyFileAttribute> <xref:System.Reflection.AssemblyKeyNameAttribute> bulunduğu yere bağlı olarak özniteliği veya özniteliği kullanabilirsiniz.  
  
- Derleyici seçeneklerini kullanarak.  
  
 Bir derlemeye katı bir ad atamak için bir şifreleme anahtarı çiftiniz olması gerekir. Anahtar çifti oluşturma hakkında daha fazla bilgi için [bkz.](create-public-private-key-pair.md)  
  
## <a name="create-and-sign-an-assembly-with-a-strong-name-by-using-visual-studio"></a>Visual Studio'u kullanarak güçlü bir ada sahip bir derleme oluşturma ve imzalama  
  
1. **Çözüm Gezgini'nde,** proje için kısayol menüsünü açın ve ardından **Özellikler'i**seçin.  
  
2. **İmzala** sekmesini seçin.  
  
3. Montaj kutusunu **Imzala'yı** seçin.  
  
4. Güçlü **bir ad anahtarı dosya** kutusunu seçin, **Gözat'ı**seçin ve ardından anahtar dosyasına gidin. Yeni bir anahtar dosyası oluşturmak için **Yeni'yi** seçin ve **Adını Güçlü Ad Anahtarı Oluştur** iletişim kutusuna girin.  
  
> [!NOTE]
> [Bir derlemeyi imzalamayı geciktirmek](delay-sign.md)için ortak anahtar dosyası seçin.  
  
### <a name="create-and-sign-an-assembly-with-a-strong-name-by-using-the-assembly-linker"></a>Derleme Bağlantı Cılız'ı kullanarak güçlü bir ada sahip bir derleme oluşturma ve imzalama  
  
Visual [Studio için Geliştirici Komut Komut Ustem'inde](../../framework/tools/developer-command-prompt-for-vs.md)aşağıdaki komutu girin:  

**al** **/out:**\<*assemblyName*> *\<moduleName>* **/keyfile:**\<*keyfileName*>  

Konumlar:  

- *assemblyName,* Assembly Linker'ın yarayacağı güçlü bir şekilde imzalanmış derlemenin *(.dll* veya *.exe* dosyası) adıdır.  
  
- *moduleName,* bir veya daha fazla tür içeren bir .NET Framework kod modülünün *(.netmodule* dosyası) adıdır. C# veya Visual `/target:module` Basic'teki anahtarla kodunuzu derleyerek bir *.netmodule* dosyası oluşturabilirsiniz.
  
- *keyfileName* anahtar çiftini içeren kapsayıcı veya dosyanın adıdır. Derleme Bağlantıcısı, geçerli dizine göre göreli bir yolu yorumlar.  

Aşağıdaki örnek anahtar *dosyasgKey.snk*kullanarak güçlü bir ad ile derleme *MyAssembly.dll* imzalar.  

```console
al /out:MyAssembly.dll MyModule.netmodule /keyfile:sgKey.snk  
```  
  
Bu araç hakkında daha fazla bilgi için [Derleme Bağlantı Cısı'na](../../framework/tools/al-exe-assembly-linker.md)bakın.  
  
## <a name="sign-an-assembly-with-a-strong-name-by-using-attributes"></a>Öznitelikleri kullanarak güçlü bir ada sahip bir derleme yi imzalama  
  
1. Kaynak <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=nameWithType> kod <xref:System.Reflection.AssemblyKeyNameAttribute> dosyanıza veya özniteliğinizi ekleyin ve derlemeyi güçlü bir adla imzalarken kullanılacak anahtar çiftini içeren dosyanın veya kapsayıcının adını belirtin.  

2. Kaynak kodu normal şekilde derleyin.  

   > [!NOTE]
   > C# ve Visual Basic derleyicileri, kaynak kodundaki <xref:System.Reflection.AssemblyKeyFileAttribute> veya <xref:System.Reflection.AssemblyKeyNameAttribute> öznitelikteki öznitelikle karşılaştıklarında derleyici uyarıları (sırasıyla CS1699 ve BC41008) verirler. Uyarıları gözardı edebilirsiniz.  

Aşağıdaki örnek, <xref:System.Reflection.AssemblyKeyFileAttribute> derlemenin derlendiği dizinde bulunan *keyfile.snk*adlı anahtar dosyasıyla özniteliği kullanır.  

```cpp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")];
```

```csharp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")]
```

```vb
<Assembly:AssemblyKeyFileAttribute("keyfile.snk")>
```

Ayrıca kaynak dosyanızı derlerken bir derlemeyi imzalamayı erteleyebilirsiniz. Daha fazla bilgi için bir [derlemeyi Geciktir-imzalayın.](delay-sign.md)  

## <a name="sign-an-assembly-with-a-strong-name-by-using-the-compiler"></a>Derleyiciyi kullanarak güçlü bir ada sahip bir derleme yi imzalama  

Kaynak kod dosyanızı veya dosyalarınızı C# ve Visual Basic'teki `/keyfile` veya C++'daki `/delaysign` `/KEYFILE` veya `/DELAYSIGN` bağlayıcı seçeneğinde veya derleyici seçeneğiyle derleyin. Seçenek adından sonra, iki nokta işareti ve anahtar dosyasının adını ekleyin. Komut satırı derleyicileri kullanırken, anahtar dosyasını kaynak kodu dosyalarınızı içeren dizine kopyalayabilirsiniz.  

Gecikme imzalama hakkında bilgi için, [bir derlemeyi Geciktir-imzalayın'](delay-sign.md)a bakın.  

Aşağıdaki örnek, C# derleyicisini kullanır ve *anahtar dosyasgKey.snk*kullanarak güçlü bir adla derleme *UtilityLibrary.dll* imzalar.  

```cmd
csc /t:library UtilityLibrary.cs /keyfile:sgKey.snk  
```  

## <a name="see-also"></a>Ayrıca bkz.

- [Tanımlayıcı adlı derlemeler oluşturma ve kullanma](create-use-strong-named.md)
- [Nasıl yapilir: Genel-özel anahtar çifti oluşturma](create-public-private-key-pair.md)
- [Al.exe (Bütünleştirilmiş Kod Bağlayıcı)](../../framework/tools/al-exe-assembly-linker.md)
- [Derlemeyi gecikmeli imzalama](delay-sign.md)
- [Derleme ve bildirim imzalamayı yönetme](/visualstudio/ide/managing-assembly-and-manifest-signing)
- [İmza lama sayfası, Proje Tasarımcısı](/visualstudio/ide/reference/signing-page-project-designer)
