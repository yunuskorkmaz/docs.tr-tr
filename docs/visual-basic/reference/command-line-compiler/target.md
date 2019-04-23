---
title: -target (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- target compiler options [Visual Basic]
- -target compiler options [Visual Basic]
- /target compiler options [Visual Basic]
ms.assetid: e0954147-548b-461f-9c4b-a8f88845616c
ms.openlocfilehash: c91e69e3d9f17f758990b8385f6b8d0a1c03bef6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59344747"
---
# <a name="-target-visual-basic"></a>-target (Visual Basic)
Derleyici çıktı biçimi belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
-target:{exe | library | module | winexe | appcontainerexe | winmdobj}  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Aşağıdaki tabloda özetlenmiştir etkisini `-target` seçeneği.  
  
|**Seçeneği**|**Davranışı**|  
|----------------|------------------|  
|`-target:exe`|Bir çalıştırılabilir konsol uygulaması oluşturmak derleyicinin neden olur.<br /><br /> Hayır, varsayılan seçenek budur `-target` seçeneği belirtildi. Yürütülebilir dosyanın .exe uzantılı oluşturulur.<br /><br /> İle aksi belirtilmediği sürece `/out` seçeneği, çıkış dosyası adını içeren giriş dosyasının adını alır `Sub Main` yordamı.<br /><br /> Yalnızca bir `Sub Main` yordam gerekli kaynak kodu dosyalarında bir .exe dosyasına derlenir. Kullanım `-main` hangi sınıfı içeren belirtmek için derleyici seçeneği `Sub Main` yordamı.|  
|`-target:library`|Bir dinamik bağlantı kitaplığı (DLL) oluşturmak derleyicinin neden olur.<br /><br /> Dinamik bağlantı kitaplığı dosyası, .dll uzantısıyla oluşturulur.<br /><br /> İle aksi belirtilmediği sürece `-out` seçeneği, çıkış dosyası adı ilk giriş dosyasının adını alır.<br /><br /> Bir DLL oluştururken bir `Sub Main` yordam gerekli değildir.|  
|`-target:module`|Bir derlemeye eklenebilir bir modül derleyici neden olur.<br /><br /> Çıkış dosyası, bir .netmodule uzantısı ile oluşturulur.<br /><br /> .NET ortak dil çalışma zamanı derleme yok. bir dosya yüklenemiyor. Bir derlemenin derleme bildirimine kullanarak bu tür bir dosya ancak birleştirebilirsiniz `-reference`.<br /><br /> Başka bir modül iç türleri bir modülde kod başvuruda bulunduğunda, her iki modül bir derleme bildirimine kullanarak birleştirilmesi gerekir `-reference`.<br /><br /> [- Addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) seçenek, bir modülden meta verileri alır.|  
|`-target:winexe`|Windows tabanlı yürütülebilir bir uygulama oluşturmak derleyicinin neden olur.<br /><br /> Yürütülebilir dosyanın .exe uzantılı oluşturulur. Bir kullanıcı arabiriminden ya da sağlayan bir Windows tabanlı bir uygulama olan [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] sınıf kitaplığı veya Windows API'leri ile.<br /><br /> İle aksi belirtilmediği sürece `-out` seçeneği, çıkış dosyası adını içeren giriş dosyasının adını alır `Sub Main` yordamı.<br /><br /> Yalnızca bir `Sub Main` yordam gerekli kaynak kodu dosyalarında bir .exe dosyasına derlenir. Kodunuzun sahip birden fazla sınıf sahip olduğu durumlarda bir `Sub Main` yordamı, kullanım `-main` hangi sınıfı içeren belirtmek için derleyici seçeneği `Sub Main` yordamı|  
|`-target:appcontainerexe`|Bir uygulama kapsayıcısında çalıştırılması gereken yürütülebilir Windows tabanlı bir uygulama oluşturmak derleyicinin neden olur. Bu ayar için kullanılmak üzere tasarlanmıştır [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] uygulamalar.<br /><br /> **Appcontainerexe** ayarı özellikleri alanında bir bit ayarlar [Taşınabilir Çalıştırılabilir](/windows/desktop/Debug/pe-format) dosya. Bu bit uygulama bir uygulama kapsayıcısında çalıştırılması gerektiğini belirtir. Bu bit ayarlandığında, hata oluşur `CreateProcess` yöntemi uygulama kapsayıcısı dışında uygulamayı başlatmak dener. Bu bit ayarı dışında **-target: appcontainerexe** eşdeğerdir **-target: winexe**.<br /><br /> Yürütülebilir dosyanın .exe uzantılı oluşturulur.<br /><br /> Kullanarak, aksini belirtmediğiniz sürece `-out` seçeneği, çıkış dosyası adını içeren giriş dosyasının adını alır `Sub Main` yordamı.<br /><br /> Yalnızca bir `Sub Main` yordam gerekli kaynak kodu dosyalarında bir .exe dosyasına derlenir. Birden fazla sınıf kod içerip içermediğini bir `Sub Main` yordamı, kullanım `-main` hangi sınıfı içeren belirtmek için derleyici seçeneği `Sub Main` yordamı|  
|`-target:winmdobj`|Bir Windows çalışma zamanı (.winmd) ikili dosyasına dönüştürebileceğiniz bir ara dosyası oluşturmak derleyicinin neden olur. .Winmd dosyası yönetilen dil programlarının yanı sıra, JavaScript ve C++ programları tarafından tüketilebilir.<br /><br /> Bir .winmdobj uzantısıyla Ara dosyası oluşturulur.<br /><br /> Kullanarak, aksini belirtmediğiniz sürece `-out` seçeneği, çıkış dosyası adı ilk giriş dosyasının adını alır. A `Sub Main` yordam gerekli değildir.<br /><br /> .Winmdobj dosyası için giriş olarak kullanılmak üzere tasarlanmıştır <xref:Microsoft.Build.Tasks.WinMDExp> dışa aktarma aracı bir Windows meta veri (WinMD) dosyası. WinMD dosyası bir .winmd uzantısı olduğundan ve, JavaScript, C++ ve Windows çalışma zamanı kullanmak kod özgün kitaplık ve WinMD tanımları içerir.|  
  
 Siz belirtmediğiniz sürece `-target:module`, `-target` neden olan bir [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] bütünleştirilmiş kod bildirimi için bir çıktı dosyası eklenecek.  
  
 Vbc.exe her bir örneğini oluşturur, en fazla bir çıkış dosyası. Gibi bir derleyici seçeneğini belirtirseniz `-out` veya `-target` birden fazla kez, derleyici işlemleri yürürlüğe koymak sonuncu. Bir derlemede tüm dosyaları hakkında bilgi bildirimine eklenir. Tüm dosyaları ile oluşturulanlar dışındaki çıktı `-target:module` bildirimindeki derleme metaverilerini içerir. Kullanım [Ildasm.exe (IL ayrıştırıcı)](../../../framework/tools/ildasm-exe-il-disassembler.md) bir çıkış dosyası meta verileri görüntüleyebilirsiniz.  
  
 Kısa formunu da `-target` olduğu `-t`.  
  
### <a name="to-set--target-in-the-visual-studio-ide"></a>Visual Studio IDE'de ayarlamak için - hedef  
  
1. Seçili bir projeyi **Çözüm Gezgini**. Üzerinde **proje** menüsünü tıklatın **özellikleri**.   
  
2. Tıklayın **uygulama** sekmesi.  
  
3. Değer değiştirme **uygulama türü** kutusu.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod derlenir `in.vb`, oluşturma `in.dll`:  
  
```console
vbc -target:library in.vb  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [-main](../../../visual-basic/reference/command-line-compiler/main.md)
- [-out (Visual Basic)](../../../visual-basic/reference/command-line-compiler/out.md)
- [-başvuru (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
- [-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)
- [-moduleassemblyname](../../../visual-basic/reference/command-line-compiler/moduleassemblyname.md)
- [.NET’te bütünleştirilmiş kodlar](../../../standard/assembly/index.md)
- [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
