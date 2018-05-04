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
ms.openlocfilehash: 45f8ad3bd9226ffd821fc792cdd4d0a6dac1a414
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-sign-an-assembly-with-a-strong-name"></a>Nasıl yapılır: Derlemeyi Tanımlayıcı Adla İmzalama
Bir derlemeyi katı bir adla imzalamak için çeşitli yollar vardır:  
  
-   Kullanarak **imzalama** bir projenin sekmesinde **özellikleri** Visual Studio'da iletişim kutusu. Bu, bir derlemeyi katı bir adla imzalamanın en kolay ve en kullanışlı yoludur.  
  
-   Kullanarak [derleme bağlayıcı (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) bir .NET Framework kod modülüne (.netmodule dosyası) bir anahtar dosya ile ilişkilendirilecek.  
  
-   Katı ad bilgilerini kodunuza eklemek için derleme özniteliklerini kullanarak. Kullanabilirsiniz <xref:System.Reflection.AssemblyKeyFileAttribute> veya <xref:System.Reflection.AssemblyKeyNameAttribute> bulunduğu konuma bağlı olarak kullanılacak anahtar dosyası özniteliği.  
  
-   Derleyici seçeneklerini kullanarak.  
  
 Bir derlemeye katı bir ad atamak için bir şifreleme anahtarı çiftiniz olması gerekir. Bir anahtar çifti oluşturma hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir genel-özel anahtar çifti oluşturma](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md).  
  
### <a name="to-create-and-sign-an-assembly-with-a-strong-name-by-using-visual-studio"></a>Visual Studio'yu kullanarak bir derleme oluşturmak ve katı bir adla imzalamak için  
  
1.  İçinde **Çözüm Gezgini**projesi için kısayol menüsünü açın ve ardından **özellikleri**.  
  
2.  Seçin **imzalama** sekmesi.  
  
3.  Seçin **derlemeyi imzalamak** kutusu.  
  
4.  İçinde **güçlü ad anahtar dosyası seçin** kutusunda, seçin  **\<Gözat... >** ve ardından anahtar dosyasına gidin. Yeni bir anahtar dosyası oluşturmak için seçtiğiniz  **\<yeni... >** ve adını girin **güçlü ad anahtarı oluştur** iletişim kutusu.  
  
### <a name="to-create-and-sign-an-assembly-with-a-strong-name-by-using-the-assembly-linker"></a>Derleme Bağlayıcısı'nı kullanarak bir derleme oluşturmak ve derlemeyi güçlü bir adla imzalamak için  
  
-   Konumundaki [Visual Studio komut istemi](../../../docs/framework/tools/developer-command-prompt-for-vs.md), aşağıdaki komutu yazın:  
  
     **Al** **/out:**\<*assemblyName*> *\<moduleName >* **/keyfile:** \<  *keyfileName*>  
  
     burada:  
  
     *AssemblyName*  
     Assembly Linker'in yayacağı katı imzalı derlemenin (.dll veya .exe dosyası) adı.  
  
     *Modül adı*  
     Bir veya birden çok tür içeren bir .NET Framework kod modülünün (bir .netmodule dosyası) adı. Kodunuzu derlerken tarafından .netmodule dosyası oluşturabilirsiniz `/target:module` C# veya Visual Basic geçiş yapın.  
  
     *keyfileName*  
     Anahtar çiftini içeren kapsayıcının veya dosyanın adı. Assembly Linker, geçerli dizinle ilişki içindeki bir göreli yolu yorumlar.  
  
 Aşağıdaki örnek derleme imzalar `MyAssembly.dll` anahtar dosyası kullanarak bir güçlü ad ile `sgKey.snk`.  
  
```  
al /out:MyAssembly.dll MyModule.netmodule /keyfile:sgKey.snk  
```  
  
 Bu araç hakkında daha fazla bilgi için bkz: [derleme bağlayıcı](../../../docs/framework/tools/al-exe-assembly-linker.md).  
  
#### <a name="to-sign-an-assembly-with-a-strong-name-by-using-attributes"></a>Bir derlemeyi öznitelikleri kullanarak bir katı adla imzalamak için  
  
1.  Ekleme <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=nameWithType> veya <xref:System.Reflection.AssemblyKeyNameAttribute> özniteliği, kaynak kodu dosyasına ve derlemeyi tanımlayıcı adla imzalama sırasında kullanmak için anahtar çiftini içeren kapsayıcı ve dosya adını belirtin.  
  
2.  Kaynak kodu normal şekilde derleyin.  
  
> [!NOTE]
>  C# ve Visual Basic derleyicileri derleyici uyarıları sorun (CS1699 ve BC41008, sırasıyla) ne zaman karşılaştıkları <xref:System.Reflection.AssemblyKeyFileAttribute> veya <xref:System.Reflection.AssemblyKeyNameAttribute> kaynak kodunda özniteliği. Uyarıları gözardı edebilirsiniz.  
  
 Aşağıdaki örnek kullanır <xref:System.Reflection.AssemblyKeyFileAttribute> adlı bir anahtar dosyası özniteliğiyle `keyfile.snk`, derleme derlenmiş burada dizininde bulunur.  
  
 [!code-cpp[AssemblyName_KeyPair#21](../../../samples/snippets/cpp/VS_Snippets_CLR/AssemblyName_KeyPair/CPP/keyfileattrib.cpp#21)]
 [!code-csharp[AssemblyName_KeyPair#21](../../../samples/snippets/csharp/VS_Snippets_CLR/AssemblyName_KeyPair/CS/keyfileattrib.cs#21)]
 [!code-vb[AssemblyName_KeyPair#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AssemblyName_KeyPair/VB/keyfileattrib.vb#21)]  
  
 Ayrıca kaynak dosyanızı derlerken bir derlemeyi imzalamayı erteleyebilirsiniz. Daha fazla bilgi için bkz: [Gecikmeli bir derleme imzalama](../../../docs/framework/app-domains/delay-sign-assembly.md).  
  
### <a name="to-sign-an-assembly-with-a-strong-name-by-using-the-compiler"></a>Bir derlemeyi derleyiciyi kullanarak bir katı adla imzalamak için  
  
-   Kaynak kodu dosyasının veya dosyaları derleme `/keyfile` veya `/delaysign` C# ve Visual Basic derleyici seçeneği veya `/KEYFILE` veya `/DELAYSIGN` c++ bağlayıcı seçeneği. Seçenek adından sonra, iki nokta işareti ve anahtar dosyasının adını ekleyin. Komut satırı derleyicileri kullanırken, anahtar dosyasını kaynak kodu dosyalarınızı içeren dizine kopyalayabilirsiniz.  
  
     Gecikmeli imzalama hakkında daha fazla bilgi için bkz: [Gecikmeli bir derleme imzalama](../../../docs/framework/app-domains/delay-sign-assembly.md).  
  
     Aşağıdaki örnek C# Derleyici kullanır ve derleme imzalar `UtilityLibrary.dll` anahtar dosyası kullanarak bir güçlü ad ile `sgKey.snk`.  
  
    ```  
    csc /t:library UtilityLibrary.cs /keyfile:sgKey.snk  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kesin Adlandırılmış Bütünleştirilmiş Kodlar Oluşturma ve Kullanma](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)  
 [Nasıl yapılır: Genel-Özel Anahtar Çifti Oluşturma](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md)  
 [Al.exe (Bütünleştirilmiş Kod Bağlayıcı)](../../../docs/framework/tools/al-exe-assembly-linker.md)  
 [Bütünleştirilmiş Kod İmzalamayı Geciktirme](../../../docs/framework/app-domains/delay-sign-assembly.md)  
 [Derleme ve Bildirim İmzalamayı Yönetme](/visualstudio/ide/managing-assembly-and-manifest-signing)  
 [İmzalama Sayfası, Proje Tasarımcısı](https://msdn.microsoft.com/library/0k50fs3b)
