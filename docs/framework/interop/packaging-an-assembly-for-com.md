---
title: COM için Derlemeyi Paketleme
ms.date: 03/30/2017
helpviewer_keywords:
- exposing .NET Framework components to COM
- COM interop, packaging assemblies
- packaging assemblies for COM
- Tlbexp.exe
- TypeLibConverter class
- .NET Services Installation tool
- Assembly Registration tool
- Type Library Exporter
- Reqsvcs.exe
- interoperation with unmanaged code, exposing .NET Framework components
- interoperation with unmanaged code, packaging assemblies
- COM interop, exposing COM components
- Reqasm.exe
ms.assetid: 39dc55aa-f2a1-4093-87bb-f1c0edb6e761
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cb45fc253e24c9770436432d2734ba8fce249453
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67662363"
---
# <a name="packaging-an-assembly-for-com"></a>COM için Derlemeyi Paketleme

COM geliştiricilerin uygulamalarında birleştirmek planladıkları yönetilen türleri hakkında aşağıdaki bilgileri yararlı olabilir:

- COM uygulamaları tüketebileceği türlerinin bir listesi

  Bazı yönetilen türlerin, COM görünmez; Bazı görünür ancak değil; ve bazı görünür ve oluşturulabilir. Derleme türleri görünmez, görünür değil ve oluşturulabilir herhangi bir birleşimini içerebilir. Eksiksiz olması için özellikle bu türleri .NET Framework için kullanıma türlerin bir alt kümesi olduğunda, COM kullanıma sunmak istediğiniz derleme türlerini tanımlayın.

  Ek bilgi için bkz: [birlikte çalışma için .NET türlerini niteleme](qualifying-net-types-for-interoperation.md).

- Sürüm oluşturma yönergeleri

  (Bir COM birlikte çalışma tarafından üretilen arabirimi) sınıf arabirimi uygulayan yönetilen sınıflar, sürüm oluşturma kısıtlamalar geçerlidir.

  Sınıf arabirimi kullanma ile ilgili yönergeler için bkz: [sınıf arabirimine giriş](com-callable-wrapper.md#introducing-the-class-interface).

- Dağıtım yönergeleri

  Bir yayımcı tarafından imzalanmış tanımlayıcı adlandırılmış derlemeler genel derleme önbelleğine yüklenebilir. İmzasız derlemeler kullanıcının makinesine özel derlemeler yüklenmesi gerekir.

  Ek bilgi için bkz: [derleme güvenlik konuları](../app-domains/assembly-security-considerations.md).

- Tür kitaplığı ekleme

  Çoğu türleri COM uygulama tarafından kullanılan, bir tür kitaplığı gerektirir. Bir tür kitaplığı oluşturabilir veya bu görevi gerçekleştirmek COM geliştiriciler. Windows Yazılım Geliştirme Seti (SDK), bir tür kitaplığı oluşturmak için aşağıdaki seçenekleri sağlar:

  - [Tür kitaplığı dışarı Aktarıcı](#cpconpackagingassemblyforcomanchor1)

  - [TypeLibConverter sınıfı](#cpconpackagingassemblyforcomanchor2)

  - [Derleme kayıt aracı](#cpconpackagingassemblyforcomanchor3)

  - [.NET Hizmetleri Yükleme aracı](#cpconpackagingassemblyforcomanchor4)

  Seçtiğiniz mekanizması bağımsız olarak, oluşturulan tür kitaplığı'nda yalnızca sağladığınız derlemede tanımlanan ortak türler dahil edilir.

Yönergeler için [nasıl yapılır: Tür kitaplıkları Win32 kaynakları olarak ekleyin. AĞ tabanlı uygulamalar](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ww9a897z(v=vs.100)).

<a name="cpconpackagingassemblyforcomanchor1"></a>

## <a name="type-library-exporter"></a>Tür Kitaplığı Dışarı Aktarıcı

[Tür kitaplığı dışarı Aktarıcı (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md) sınıflar ve arabirimler COM türü kitaplık bir derlemede yer alan dönüştürür bir komut satırı aracıdır. Sınıf türü bilgileri kullanılabilir olduğunda, COM istemcilerinin .NET sınıfının bir örneğini oluşturabilir ve bir COM nesnesi sanki olarak örnek yöntemlerini çağırmaya. Tlbexp.exe, tek seferde tüm bütünleştirilmiş dönüştürür. Derlemede tanımlanan türlerin bir alt kümesi için tür bilgisi üretmek üzere Tlbexp.exe'yi kullanamazsınız.

<a name="cpconpackagingassemblyforcomanchor2"></a>

## <a name="typelibconverter-class"></a>TypeLibConverter sınıfı

<xref:System.Runtime.InteropServices.TypeLibConverter> Bulunan sınıf **System.Runtime.Interop** ad alanı, sınıflar ve arabirimler COM türü kitaplık bir derlemede yer alan dönüştürür. Bu API önceki bölümde açıklanan tür kitaplığı verici aynı tür bilgileri üretir.

**TypeLibConverter sınıfı** uygulayan <xref:System.Runtime.InteropServices.ITypeLibConverter>.

<a name="cpconpackagingassemblyforcomanchor3"></a>

## <a name="assembly-registration-tool"></a>Derleme kayıt aracı

[Derleme Kayıt Aracı (Regasm.exe)](../tools/regasm-exe-assembly-registration-tool.md) oluşturabilir ve uyguladığınızda, tür kitaplığını kaydetmek **/TLB:** seçeneği. COM istemcileri Windows kayıt defterinde tür kitaplıkları yüklü olmasını gerektirir. Bu seçenek olmadan, Regasm.exe türleri yalnızca bir derleme, tür kitaplığını kaydeder. Bir derlemede türlerini kaydetme ve tür kitaplığı kaydı ayrı etkinliklerdir.

<a name="cpconpackagingassemblyforcomanchor4"></a>

## <a name="net-services-installation-tool"></a>.NET Hizmetleri Yükleme aracı

[.NET Hizmetleri Yükleme aracı (Regsvcs.exe)](../tools/regsvcs-exe-net-services-installation-tool.md) yönetilen sınıflar için Windows 2000 Bileşen Hizmetleri ekler ve tek bir araçla içindeki çeşitli görevleri birleştirir. Yükleme ve derlemeyi kaydettirdikten ek olarak, Regsvcs.exe oluşturmak, kaydedin ve var olan bir COM + 1.0 uygulamasına tür kitaplığını yükleyin.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.InteropServices.TypeLibConverter>
- <xref:System.Runtime.InteropServices.ITypeLibConverter>
- [.NET Framework Bileşenlerini COM'da Gösterme](exposing-dotnet-components-to-com.md)
- [Birlikte Çalışma için .NET Türlerini Niteleme](qualifying-net-types-for-interoperation.md)
- [Sınıf arabirimine giriş](com-callable-wrapper.md#introducing-the-class-interface)
- [Bütünleştirilmiş Kod Güvenliği Konuları](../app-domains/assembly-security-considerations.md)
- [Tlbexp.exe (Tür Kitaplığı Dışarı Aktarıcı)](../tools/tlbexp-exe-type-library-exporter.md)
- [Bütünleştirilmiş Kodları COM ile Kaydetme](registering-assemblies-with-com.md)
- [Nasıl yapılır: Tür kitaplıklarını uygulamalarda Win32 kaynakları olarak katıştırma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ww9a897z(v=vs.100))
