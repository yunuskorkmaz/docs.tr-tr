---
title: 'Nasıl yapılır: Derlemeyi Tanımlayıcı Adla İmzalama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- strong-named assemblies, signing with strong names
- signing assemblies
- assemblies [.NET Framework], signing
- assemblies [.NET Framework], strong-named
ms.assetid: 2c30799a-a826-46b4-a25d-c584027a6c67
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0b109ec82d139e3b3eb321c90d5f41dd1eae216f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927928"
---
# <a name="how-to-sign-an-assembly-with-a-strong-name"></a>Nasıl yapılır: Derlemeyi Tanımlayıcı Adla İmzalama
Bir derlemeyi katı bir adla imzalamak için çeşitli yollar vardır:  
  
- Visual Studio 'da bir projenin **Özellikler** Iletişim kutusunda **imzalama** sekmesini kullanarak. Bu, bir derlemeyi katı bir adla imzalamanın en kolay ve en kullanışlı yoludur.  
  
- Bir .NET Framework kodu modülünü (. netmodule dosyası) anahtar dosyasıyla bağlamak için [derleme Bağlayıcısı (al. exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) kullanarak.  
  
- Katı ad bilgilerini kodunuza eklemek için derleme özniteliklerini kullanarak. Kullanılacak anahtar dosyasının bulunduğu yere <xref:System.Reflection.AssemblyKeyFileAttribute> bağlı olarak <xref:System.Reflection.AssemblyKeyNameAttribute> ya da özniteliğini kullanabilirsiniz.  
  
- Derleyici seçeneklerini kullanarak.  
  
 Bir derlemeye katı bir ad atamak için bir şifreleme anahtarı çiftiniz olması gerekir. Anahtar çifti oluşturma hakkında daha fazla bilgi için bkz [. nasıl yapılır: Ortak özel anahtar çifti](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md)oluşturun.  
  
### <a name="to-create-and-sign-an-assembly-with-a-strong-name-by-using-visual-studio"></a>Visual Studio'yu kullanarak bir derleme oluşturmak ve katı bir adla imzalamak için  
  
1. **Çözüm Gezgini**' de, proje için kısayol menüsünü açın ve ardından **Özellikler**' i seçin.  
  
2. **İmzalama** sekmesini seçin.  
  
3. **Derlemeyi imzala** kutusunu seçin.  
  
4. **Tanımlayıcı ad seçin anahtar dosyası** kutusunda,  **\<araştır... ' ı seçin. >** ve ardından anahtar dosyasına gidin. Yeni bir anahtar dosyası oluşturmak için  **\<yeni... öğesini seçin. >** ve adını **tanımlayıcı ad anahtarı oluştur** iletişim kutusuna girin.  
  
> [!NOTE]
> [Bir derlemeyi imzalamayı geciktirmek](../../../docs/framework/app-domains/delay-sign-assembly.md)için bir ortak anahtar dosyası seçin.  
  
### <a name="to-create-and-sign-an-assembly-with-a-strong-name-by-using-the-assembly-linker"></a>Derleme Bağlayıcısı'nı kullanarak bir derleme oluşturmak ve derlemeyi güçlü bir adla imzalamak için  
  
- [Visual Studio için geliştirici komut istemi](../../../docs/framework/tools/developer-command-prompt-for-vs.md), aşağıdaki komutu yazın:  
  
     **Al** **/Out:** \<AssemblyNameModuleName> > **/keyfile**:keyfilename\< *\<* >  
  
     burada:  
  
     *assemblyName*  
     Assembly Linker'in yayacağı katı imzalı derlemenin (.dll veya .exe dosyası) adı.  
  
     *Ladı*  
     Bir veya birden çok tür içeren bir .NET Framework kod modülünün (bir .netmodule dosyası) adı. Kodunuzu `/target:module` veya Visual Basic içindeki C# anahtarla derleyerek bir. netmodule dosyası oluşturabilirsiniz.  
  
     *Anahtar dosya adı*  
     Anahtar çiftini içeren kapsayıcının veya dosyanın adı. Assembly Linker, geçerli dizinle ilişki içindeki bir göreli yolu yorumlar.  
  
 Aşağıdaki örnek, anahtar dosyasını `MyAssembly.dll` `sgKey.snk`kullanarak derlemeyi tanımlayıcı bir adla imzalar.  
  
```  
al /out:MyAssembly.dll MyModule.netmodule /keyfile:sgKey.snk  
```  
  
 Bu araç hakkında daha fazla bilgi için bkz. [derleme Bağlayıcısı](../../../docs/framework/tools/al-exe-assembly-linker.md).  
  
#### <a name="to-sign-an-assembly-with-a-strong-name-by-using-attributes"></a>Bir derlemeyi öznitelikleri kullanarak bir katı adla imzalamak için  
  
1. Kaynak kodu dosyanıza <xref:System.Reflection.AssemblyKeyNameAttribute>orözniteliğini ekleyin ve derlemeyi tanımlayıcı bir adla imzalarken kullanılacak anahtar çiftini içeren dosya veya kapsayıcının adını belirtin. <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=nameWithType>  
  
2. Kaynak kodu normal şekilde derleyin.  
  
> [!NOTE]
> C# Ve Visual Basic derleyicileri, kaynak kodundaki <xref:System.Reflection.AssemblyKeyFileAttribute> veya <xref:System.Reflection.AssemblyKeyNameAttribute> özniteliğiyle karşılaştığında derleyici uyarılarını (sırasıyla CS1699 ve BC41008) yayınlarlar. Uyarıları gözardı edebilirsiniz.  
  
 Aşağıdaki örnek <xref:System.Reflection.AssemblyKeyFileAttribute> özniteliği, derlemenin derlendiği dizinde bulunan adlı `keyfile.snk`bir anahtar dosyası ile kullanır.  
  
 [!code-cpp[AssemblyName_KeyPair#21](../../../samples/snippets/cpp/VS_Snippets_CLR/AssemblyName_KeyPair/CPP/keyfileattrib.cpp#21)]
 [!code-csharp[AssemblyName_KeyPair#21](../../../samples/snippets/csharp/VS_Snippets_CLR/AssemblyName_KeyPair/CS/keyfileattrib.cs#21)]
 [!code-vb[AssemblyName_KeyPair#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AssemblyName_KeyPair/VB/keyfileattrib.vb#21)]  
  
 Ayrıca kaynak dosyanızı derlerken bir derlemeyi imzalamayı erteleyebilirsiniz. Daha fazla bilgi için bkz. [bir derlemeyi IMZALAMAYı geciktirme](../../../docs/framework/app-domains/delay-sign-assembly.md).  
  
### <a name="to-sign-an-assembly-with-a-strong-name-by-using-the-compiler"></a>Bir derlemeyi derleyiciyi kullanarak bir katı adla imzalamak için  
  
- Kaynak `/keyfile` kodu dosyanızı veya dosyalarınızı, veya Visual Basic içindeki C# or `/delaysign` derleyici seçeneğiyle veya `/KEYFILE` ' de `/DELAYSIGN` C++veya bağlayıcı seçeneğinde derleyin. Seçenek adından sonra, iki nokta işareti ve anahtar dosyasının adını ekleyin. Komut satırı derleyicileri kullanırken, anahtar dosyasını kaynak kodu dosyalarınızı içeren dizine kopyalayabilirsiniz.  
  
     Gecikmeli imzalama hakkında daha fazla bilgi için bkz. [bir derlemeyi IMZALAMAYı geciktirme](../../../docs/framework/app-domains/delay-sign-assembly.md).  
  
     Aşağıdaki örnek, C# derleyicisini kullanır ve anahtar dosyasını `UtilityLibrary.dll` `sgKey.snk`kullanarak derlemeyi tanımlayıcı bir adla imzalar.  
  
    ```  
    csc /t:library UtilityLibrary.cs /keyfile:sgKey.snk  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kesin Adlandırılmış Bütünleştirilmiş Kodlar Oluşturma ve Kullanma](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
- [Nasıl yapılır: Ortak özel anahtar çifti oluşturma](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md)
- [Al.exe (Bütünleştirilmiş Kod Bağlayıcı)](../../../docs/framework/tools/al-exe-assembly-linker.md)
- [Bütünleştirilmiş Kod İmzalamayı Geciktirme](../../../docs/framework/app-domains/delay-sign-assembly.md)
- [Derleme ve Bildirim İmzalamayı Yönetme](/visualstudio/ide/managing-assembly-and-manifest-signing)
- [İmzalama Sayfası, Proje Tasarımcısı](/visualstudio/ide/reference/signing-page-project-designer)
