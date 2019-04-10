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
ms.openlocfilehash: 5580b6d8af7319397ad7eb6416941c2be0dcdb76
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59303439"
---
# <a name="how-to-sign-an-assembly-with-a-strong-name"></a>Nasıl yapılır: Derlemeyi Tanımlayıcı Adla İmzalama
Bir derlemeyi katı bir adla imzalamak için çeşitli yollar vardır:  
  
-   Kullanarak **imzalama** projenin sekmede **özellikleri** Visual Studio'da iletişim kutusu. Bu, bir derlemeyi katı bir adla imzalamanın en kolay ve en kullanışlı yoludur.  
  
-   Kullanarak [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) bir .NET Framework kod modülünü (bir .netmodule dosyası) bir anahtar dosyası ile ilişkilendirilecek.  
  
-   Katı ad bilgilerini kodunuza eklemek için derleme özniteliklerini kullanarak. Kullanabilirsiniz <xref:System.Reflection.AssemblyKeyFileAttribute> veya <xref:System.Reflection.AssemblyKeyNameAttribute> kullanılacak anahtar dosyasının bulunduğu bağlı olarak özniteliği.  
  
-   Derleyici seçeneklerini kullanarak.  
  
 Bir derlemeye katı bir ad atamak için bir şifreleme anahtarı çiftiniz olması gerekir. Bir anahtar çifti oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Genel-özel anahtar çifti oluşturma](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md).  
  
### <a name="to-create-and-sign-an-assembly-with-a-strong-name-by-using-visual-studio"></a>Visual Studio'yu kullanarak bir derleme oluşturmak ve katı bir adla imzalamak için  
  
1. İçinde **Çözüm Gezgini**, proje için kısayol menüsünü açın ve ardından **özellikleri**.  
  
2. Seçin **imzalama** sekmesi.  
  
3. Seçin **derlemeyi imzalamayı** kutusu.  
  
4. İçinde **bir tanımlayıcı ad anahtar dosyası seç** kutusunda  **\<Gözat … >** ve ardından anahtar dosyasına gidin. Yeni bir anahtar dosyası oluşturmak için seçin  **\<yeni … >** ve adını girin **katı ad anahtarı oluştur** iletişim kutusu.  
  
> [!NOTE]
>  Şunları [gecikme bir derlemeyi imzalamak](../../../docs/framework/app-domains/delay-sign-assembly.md), ortak anahtar dosyası seçin.  
  
### <a name="to-create-and-sign-an-assembly-with-a-strong-name-by-using-the-assembly-linker"></a>Derleme Bağlayıcısı'nı kullanarak bir derleme oluşturmak ve derlemeyi güçlü bir adla imzalamak için  
  
-   Konumunda [Visual Studio için geliştirici komut istemi](../../../docs/framework/tools/developer-command-prompt-for-vs.md), aşağıdaki komutu yazın:  
  
     **Al** **/out:**\<*assemblyName*> *\<moduleName >* **/keyfile:** \<  *keyfileName*>  
  
     burada:  
  
     *derlemeAdı*  
     Assembly Linker'in yayacağı katı imzalı derlemenin (.dll veya .exe dosyası) adı.  
  
     *{1&gt;modülAdı&lt;1}*  
     Bir veya birden çok tür içeren bir .NET Framework kod modülünün (bir .netmodule dosyası) adı. Kodunuzu derlemek tarafından bir .netmodule dosyası oluşturabilirsiniz `/target:module` C# veya Visual Basic'te geçiş yapın.  
  
     *{1&gt;anahtardosyasıAdı&lt;1}*  
     Anahtar çiftini içeren kapsayıcının veya dosyanın adı. Assembly Linker, geçerli dizinle ilişki içindeki bir göreli yolu yorumlar.  
  
 Aşağıdaki örnek, derlemeyi imzalar `MyAssembly.dll` anahtar dosyasını kullanarak bir katı adla `sgKey.snk`.  
  
```  
al /out:MyAssembly.dll MyModule.netmodule /keyfile:sgKey.snk  
```  
  
 Bu araç hakkında daha fazla bilgi için bkz. [Assembly Linker](../../../docs/framework/tools/al-exe-assembly-linker.md).  
  
#### <a name="to-sign-an-assembly-with-a-strong-name-by-using-attributes"></a>Bir derlemeyi öznitelikleri kullanarak bir katı adla imzalamak için  
  
1. Ekleme <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=nameWithType> veya <xref:System.Reflection.AssemblyKeyNameAttribute> özniteliğini kaynak kod dosyanızın ve dosya veya derlemeyi bir katı adla imzalarken kullanılacak anahtar çiftini içeren kapsayıcının adını belirtin.  
  
2. Kaynak kodu normal şekilde derleyin.  
  
> [!NOTE]
>  C# ve Visual Basic derleyicileri sorun derleyici uyarıları (sırasıyla, CS1699 ve BC41008 sırasıyla) karşılaştıklarında <xref:System.Reflection.AssemblyKeyFileAttribute> veya <xref:System.Reflection.AssemblyKeyNameAttribute> kaynak kodundaki özniteliği. Uyarıları gözardı edebilirsiniz.  
  
 Aşağıdaki örnekte <xref:System.Reflection.AssemblyKeyFileAttribute> adlı bir anahtar dosyasıyla özniteliğiyle `keyfile.snk`, burada derlemenin derlendiği dizinde bulunur.  
  
 [!code-cpp[AssemblyName_KeyPair#21](../../../samples/snippets/cpp/VS_Snippets_CLR/AssemblyName_KeyPair/CPP/keyfileattrib.cpp#21)]
 [!code-csharp[AssemblyName_KeyPair#21](../../../samples/snippets/csharp/VS_Snippets_CLR/AssemblyName_KeyPair/CS/keyfileattrib.cs#21)]
 [!code-vb[AssemblyName_KeyPair#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AssemblyName_KeyPair/VB/keyfileattrib.vb#21)]  
  
 Ayrıca kaynak dosyanızı derlerken bir derlemeyi imzalamayı erteleyebilirsiniz. Daha fazla bilgi için [derlemeyi imzalamayı geciktirme](../../../docs/framework/app-domains/delay-sign-assembly.md).  
  
### <a name="to-sign-an-assembly-with-a-strong-name-by-using-the-compiler"></a>Bir derlemeyi derleyiciyi kullanarak bir katı adla imzalamak için  
  
-   Kaynak kod dosyanız veya dosyalarınız ile derleme `/keyfile` veya `/delaysign` C# ve Visual Basic derleyici seçeneğini veya `/KEYFILE` veya `/DELAYSIGN` c++ bağlayıcı seçeneği. Seçenek adından sonra, iki nokta işareti ve anahtar dosyasının adını ekleyin. Komut satırı derleyicileri kullanırken, anahtar dosyasını kaynak kodu dosyalarınızı içeren dizine kopyalayabilirsiniz.  
  
     Gecikmeli imzalama hakkında daha fazla bilgi için bkz: [derlemeyi imzalamayı geciktirme](../../../docs/framework/app-domains/delay-sign-assembly.md).  
  
     Aşağıdaki örnek C# derleyicisini kullanır ve derlemeyi imzalar `UtilityLibrary.dll` anahtar dosyasını kullanarak bir katı adla `sgKey.snk`.  
  
    ```  
    csc /t:library UtilityLibrary.cs /keyfile:sgKey.snk  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tanımlayıcı Adlı Derlemeler Oluşturma ve Kullanma](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
- [Nasıl yapılır: Genel-Özel Anahtar Çifti Oluşturma](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md)
- [Al.exe (Derleme Bağlayıcı)](../../../docs/framework/tools/al-exe-assembly-linker.md)
- [Derleme İmzalamayı Geciktirme](../../../docs/framework/app-domains/delay-sign-assembly.md)
- [Derleme ve Bildirim İmzalamayı Yönetme](/visualstudio/ide/managing-assembly-and-manifest-signing)
- [İmzalama Sayfası, Proje Tasarımcısı](/visualstudio/ide/reference/signing-page-project-designer)
