---
title: COM için bir .NET Framework derlemesi paketleme
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
ms.openlocfilehash: 6866da283cc7cdd180aada252007d67bd72cd862
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124091"
---
# <a name="packaging-a-net-framework-assembly-for-com"></a>COM için bir .NET Framework derlemesi paketleme

COM geliştiricileri, uygulamasında dahil etmek üzere plantıkları yönetilen türler hakkında aşağıdaki bilgilerden faydalanabilir:

- COM uygulamalarının tüketebileceği türlerin listesi

  Bazı yönetilen türler COM 'a görünmez; Bazıları görünür ancak creatable değildir; ve bazıları hem görünür hem de creatable. Bir bütünleştirilmiş kod, görünmeyen, Visible, oluşturulabilir ve oluşturulabilir türlerinin herhangi bir birleşimini içerebilir. Tamamlananlar için, özellikle bu türler .NET Framework gösterilen türlerin bir alt kümesi olduğunda, COM 'da kullanıma sunmayı planladığınız bir derlemede bulunan türleri yapın.

  Daha fazla bilgi için bkz. [birlikte çalışma için .NET türlerini niteleme](../../standard/native-interop/qualify-net-types-for-interoperation.md).

- Sürüm oluşturma yönergeleri

  Sınıf arabirimini uygulayan yönetilen sınıflar (COM birlikte çalışma tarafından oluşturulan bir arabirim) sürüm oluşturma kısıtlamalarına tabidir.

  Sınıf arabirimini kullanma hakkında yönergeler için bkz. [sınıf arabirimine giriş](../../standard/native-interop/com-callable-wrapper.md#introducing-the-class-interface).

- Dağıtım yönergeleri

  Yayımcı tarafından imzalanan tanımlayıcı adlandırılmış derlemeler, genel derleme önbelleğine yüklenebilir. İmzasız derlemelerin Kullanıcı makinesine özel derlemeler olarak yüklenmesi gerekir.

  Daha fazla bilgi için bkz. [bütünleştirilmiş kod güvenliği konuları](../../standard/assembly/security-considerations.md).

- Tür kitaplığı ekleme

  Çoğu tür bir COM uygulaması tarafından tüketilirken bir tür kitaplığı gerektirir. Bir tür kitaplığı oluşturabilir veya COM geliştiricilerinin bu görevi gerçekleştirmesini sağlayabilirsiniz. Windows SDK, bir tür kitaplığı oluşturmak için aşağıdaki seçenekleri sağlar:

  - [Tür Kitaplığı Dışarı Aktarıcı](#cpconpackagingassemblyforcomanchor1)

  - [TypeLibConverter sınıfı](#cpconpackagingassemblyforcomanchor2)

  - [Derleme Kayıt Aracı](#cpconpackagingassemblyforcomanchor3)

  - [.NET Hizmetleri Yükleme Aracı](#cpconpackagingassemblyforcomanchor4)

  Seçtiğiniz mekanizmaya bakılmaksızın, yalnızca sağladığınız derlemede tanımlanan ortak türler oluşturulan tür kitaplığına dahil edilir.

Yönergeler için bkz [. nasıl yapılır: tür kitaplıklarını Win32 kaynakları olarak ekleme. NET tabanlı uygulamalar](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ww9a897z(v=vs.100)).

<a name="cpconpackagingassemblyforcomanchor1"></a>

## <a name="type-library-exporter"></a>Tür Kitaplığı Dışarı Aktarıcı

[Tür kitaplığı verme programı (Tlbexp. exe)](../tools/tlbexp-exe-type-library-exporter.md) , bir derlemede bulunan sınıfları ve arabirimleri com tür kitaplığına dönüştüren bir komut satırı aracıdır. Sınıfın tür bilgileri kullanılabilir olduğunda, COM istemcileri .NET sınıfının bir örneğini oluşturabilir ve tıpkı bir COM nesnesi gibi, örneğin yöntemlerini çağırabilir. Tlbexp. exe bir derlemeyi tek seferde dönüştürür. Derlemede tanımlanan türlerin bir alt kümesi için tür bilgisi üretmek üzere Tlbexp.exe'yi kullanamazsınız.

<a name="cpconpackagingassemblyforcomanchor2"></a>

## <a name="typelibconverter-class"></a>TypeLibConverter sınıfı

<xref:System.Runtime.InteropServices.TypeLibConverter> **System. Runtime. Interop** ad alanında bulunan sınıfı, bir derlemede bulunan SıNıFLARı ve arabirimleri bir com tür kitaplığına dönüştürür. Bu API, önceki bölümde açıklanan tür kitaplığı verme programı ile aynı tür bilgilerini üretir.

**TypeLibConverter sınıfı** öğesini uygular <xref:System.Runtime.InteropServices.ITypeLibConverter>.

<a name="cpconpackagingassemblyforcomanchor3"></a>

## <a name="assembly-registration-tool"></a>Derleme Kayıt Aracı

[Derleme Kayıt Aracı (Regasm. exe)](../tools/regasm-exe-assembly-registration-tool.md) , **/tlb:** seçeneğini uyguladığınızda bir tür kitaplığı oluşturup kaydedebilir. COM istemcileri, tür kitaplıklarının Windows kayıt defteri 'nde yüklü olmasını gerektirir. Bu seçenek olmadan, Regasm. exe türleri tür kitaplığına değil, yalnızca bir derlemeye kaydeder. Türlerin bir derlemeye kaydedilmesi ve tür kitaplığının kaydedilmesi ayrı etkinliklerdir.

<a name="cpconpackagingassemblyforcomanchor4"></a>

## <a name="net-services-installation-tool"></a>.NET Hizmetleri Yükleme Aracı

[.Net Hizmetleri Yükleme Aracı (RegSvcs. exe)](../tools/regsvcs-exe-net-services-installation-tool.md) , Windows 2000 Bileşen hizmetlerine yönetilen sınıflar ekler ve tek bir araç içinde çeşitli görevleri birleştirir. RegSvcs. exe, bir derlemeyi yüklemeye ve kaydetmeye ek olarak, tür kitaplığını var olan bir COM+ 1,0 uygulamasına oluşturabilir, kaydedebilir ve yükleyebilir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.InteropServices.TypeLibConverter>
- <xref:System.Runtime.InteropServices.ITypeLibConverter>
- [.NET Framework Bileşenlerini COM'da Gösterme](exposing-dotnet-components-to-com.md)
- [Birlikte Çalışma için Niteleyici .NET Türleri](../../standard/native-interop/qualify-net-types-for-interoperation.md)
- [Sınıf arabirimine giriş](../../standard/native-interop/com-callable-wrapper.md#introducing-the-class-interface)
- [Bütünleştirilmiş kod güvenliği konuları](../../standard/assembly/security-considerations.md)
- [Tlbexp. exe (tür kitaplığı Dışarı Aktarıcı)](../tools/tlbexp-exe-type-library-exporter.md)
- [Derlemeleri COM ile Kaydetme](registering-assemblies-with-com.md)
- [Nasıl yapılır: uygulamalarda tür kitaplıklarını Win32 kaynakları olarak katıştırma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ww9a897z(v=vs.100))
