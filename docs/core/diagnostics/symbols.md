---
title: .NET 'teki semboller
description: .NET 'teki simgelere ve taşınabilir pdb 'leri 'a giriş
ms.date: 02/08/2021
ms.openlocfilehash: 8f217bf8b62ff12a6ea1dc6a5b14b34d8037dd2d
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2021
ms.locfileid: "104759904"
---
# <a name="symbols"></a>Simgeleri

Semboller hata ayıklama ve diğer tanılama araçları için faydalıdır. Sembol dosyalarının içerikleri diller, derleyiciler ve platformlar arasında farklılık gösterir. Çok yüksek düzey semboller, kaynak kodu ile derleyici tarafından üretilen ikili arasında bir eşlemedir. Bu eşlemeler, [Visual Studio](/visualstudio/debugger/what-is-debugging) gibi araçlar tarafından ve kaynak satır numarası bilgilerini veya yerel değişken adlarını çözümlemek için [Visual Studio Code](https://code.visualstudio.com/Docs/editor/debugging) kullanılır.

[Simgeler üzerindeki Windows belgeleri](/windows/win32/dxtecharts/debugging-with-symbols) , diğer platformlar için de birçok kavramın de aynı olmasına rağmen, Windows için semboller hakkında daha ayrıntılı bilgiler içerir.

## <a name="learn-about-nets-portable-pdb-format"></a>Hakkında bilgi edinin. NET ' in taşınabilir PDB biçimi

.NET Core yeni bir sembol dosyası (PDB) biçimi sunar-taşınabilir PDB. Yalnızca Windows olan geleneksel pdb 'leri farklı olarak, taşınabilir pdb 'leri tüm platformlarda oluşturulabilir ve okunabilir.

### <a name="what-is-a-pdb"></a>PDB nedir?

PDB dosyası, başka araçlar, özellikle hata ayıklayıcılar, ana yürütülebilir dosyada bulunan ve nasıl üretildiği hakkında bilgi sağlamak için derleyici tarafından oluşturulan yardımcı bir dosyadır. Örneğin, bir hata ayıklayıcı foo. cs satır 12 ' yi doğru yürütülebilir konuma eşlemek için bir PDB okur, böylece bir kesme noktası ayarlayabilmesini sağlar. Windows PDB biçimi uzun bir süredir vardı ve daha da eski olan diğer yerel hata ayıklama sembol biçimlerinden türetilmiştir. Kendi ömrünü yerel (C/C++) programları için bir biçim olarak başlattı. .NET Framework ilk sürümü için Windows PDB biçimi .NET desteği için genişletilmiştir.

## <a name="use-the-correct-pdb-format-for-your-scenario"></a>Senaryonuz için doğru PDB biçimini kullanın

Taşınabilir pdb 'leri veya Windows pdb 'leri her yerde desteklenmez; bu nedenle, hangi biçimin kullanılacağına karar vermek için projenizin nerede kullanılacağını ve hata ayıklamasını düşünmeniz gerekir. Her iki biçimde de kullanabilmeniz ve hata ayıklamak istediğiniz bir projeniz varsa, farklı yapı konfigürasyonları kullanabilir ve her iki tüketici türünü desteklemek için projeyi iki kez oluşturabilirsiniz.

### <a name="support-for-portable-pdbs"></a>Taşınabilir pdb 'leri için destek

Taşınabilir pdb 'leri, herhangi bir işletim sisteminde okunabilir ve yönetilen kod için önerilen sembol biçimidir, ancak desteklenmediği bazı eski araç ve uygulamalar vardır:

* .NET Framework 4.7.1 veya daha önceki sürümleri hedefleyen uygulamalar: yığın izlemeleriyle birlikte satır numaralarına (örn. bir ASP.NET hata sayfasında). Yöntemlerin adı etkilenmemiştir, yalnızca kaynak dosya adları ve satır numaraları desteklenmez.

* ILDasm veya .NET yansıtıcısı gibi .NET dederleyicilerini kullanarak kaynak satır eşlemelerini veya yerel parametre adlarını görmeyi bekliyor.

* Örneğin, WinDBG ve taşınabilir pdb 'leri gibi sembolleri okumak için kullanılan en son [DIA](/visualstudio/debugger/debug-interface-access/debug-interface-access-sdk) ve araç sürümleri, ancak eski sürüm değildir.

* Taşınabilir pdb 'leri desteklemeyen eski profil oluşturucular sürümleri olabilir.

Bu dosyaları desteklemeyen araçlar üzerinde taşınabilir pdb 'leri kullanmak için taşınabilir pdb 'leri ve Windows pdb 'leri arasında dönüştürme yapan [Pdb2Pdb](https://github.com/dotnet/symreader-converter#pdb2pdb) kullanmayı deneyebilirsiniz.

### <a name="support-for-windows-pdbs"></a>Windows pdb 'leri için destek

Windows pdb 'leri yalnızca Windows üzerinde yazılabilir veya okunabilir. Yönetilen kod için Windows pdb 'leri kullanmak artık kullanılmıyor ve yalnızca eski araçlar için gereklidir. Yalnızca taşınabilir pdb 'leri için uygulanan bazı yeni derleyici özellikleri olarak Windows pdb 'leri yerine Portable pdb 'leri kullanmanız önerilir.

## <a name="see-also"></a>Ayrıca bkz.

* [DotNet-symbol](./dotnet-symbol.md) , çerçeve ikilileri için sembol dosyalarını indirmek için kullanılabilir

* [Semboller üzerinde Windows belgeleri](/windows/win32/dxtecharts/debugging-with-symbols)
