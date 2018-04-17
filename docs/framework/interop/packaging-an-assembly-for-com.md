---
title: COM için Derlemeyi Paketleme
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
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
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5c1e3ee38f98eae46c09ec2175f3c9af01288bd2
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
---
# <a name="packaging-an-assembly-for-com"></a>COM için Derlemeyi Paketleme
COM geliştiricilerin uygulamalarında eklemenizi planladıkları yönetilen türleri hakkında aşağıdaki bilgileri yararlı:  
  
-   COM uygulamaları tüketebileceği türlerinin listesi  
  
     Bazı yönetilen türler COM görünmez; Bazı görünür ancak değil creatable; ve görünür ve creatable bazılarıdır. Bir derlemeyi görünmez, görünür, değil creatable ve creatable türleri herhangi bir birleşimini kapsayabilir. Eksiksiz olması için özellikle bu türleri için .NET Framework sunulan türlerinin bir alt olduğunda, COM kullanıma sunmak istediğiniz bir derlemesi türlerini tanımlar.  
  
     Ek bilgi için bkz: [birlikte çalışma için .NET türlerini niteleme](qualifying-net-types-for-interoperation.md).  
  
-   Sürüm oluşturma yönergeleri  
  
     Sınıf arabirimini (COM birlikte çalışma oluşturulan arabirimi) yönetilen sınıflar sürüm kısıtlamalar geçerlidir.  
  
     Sınıf arabirimi kullanma ile ilgili yönergeler için bkz: [sınıf arabirimi Tanıtımı](com-callable-wrapper.md#introducing-the-class-interface).  
  
-   Dağıtım yönergeleri  
  
     Bir yayımcı tarafından imzalanan tanımlayıcı adlı derlemeler genel derleme önbelleğine yüklenebilir. İmzasız derlemeler kullanıcının makinesinde özel derlemeler yüklenmesi gerekir.  
  
     Ek bilgi için bkz: [derleme güvenliği konuları](../app-domains/assembly-security-considerations.md).  
  
-   Tür kitaplığı ekleme  
  
     Çoğu türleri COM uygulama tarafından tüketilen olduğunda bir tür kitaplığı gerektirir. Bu görevi gerçekleştirmek COM geliştiriciler veya bir tür kitaplığı oluşturabilirsiniz. [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] Bir tür kitaplığı oluşturmak için aşağıdaki seçenekleri sağlar:  
  
    -   [Tür kitaplığı dışarı Aktarıcı](#cpconpackagingassemblyforcomanchor1)  
  
    -   [TypeLibConverter sınıfı](#cpconpackagingassemblyforcomanchor2)  
  
    -   [Derleme kayıt aracı](#cpconpackagingassemblyforcomanchor3)  
  
    -   [.NET Hizmetleri Yükleme aracı](#cpconpackagingassemblyforcomanchor4)  
  
     Seçtiğiniz mekanizması bağımsız olarak, yalnızca genel türleri sağladığınız derlemede tanımlanan oluşturulan tür kitaplığı'nda bulunur.  
  
     Tür kitaplığı ayrı bir dosya olarak paketini veya içinde Win32 kaynak dosyası olarak katıştırmak bir. NET tabanlı bir uygulama. Microsoft Visual Basic 6.0 Bu görev sizin için otomatik olarak gerçekleştirilebilir; Ancak, kullanırken [!INCLUDE[vbprvbext](../../../includes/vbprvbext-md.md)], tür kitaplığı el ile ekleme. Yönergeler için bkz [nasıl yapılır: tür kitaplıklarını Win32 kaynak olarak ekleme. NET tabanlı uygulamalar](https://msdn.microsoft.com/library/c97b4b8c-2ab7-4ac7-8fc8-0ba5c5d59c44(v=vs.100)).  
  
<a name="cpconpackagingassemblyforcomanchor1"></a>   
## <a name="type-library-exporter"></a>Tür Kitaplığı Dışarı Aktarıcı  
 [Tür kitaplığı dışarı Aktarıcı (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md) sınıflar ve arabirimler COM tür kitaplığının derlemedeki bulunan dönüştüren bir komut satırı aracıdır. Sınıf türü bilgileri kullanılabilir olduğunda, COM istemcileri .NET sınıfının bir örneği oluşturun ve yeni bir COM nesnesi kabul edildiğinde örneğinin yöntemlerini çağırın. Tlbexp.exe aynı anda tüm bütünleştirilmiş dönüştürür. Derlemede tanımlanan türlerin bir alt kümesi için tür bilgisi üretmek üzere Tlbexp.exe'yi kullanamazsınız.  
  
<a name="cpconpackagingassemblyforcomanchor2"></a>   
## <a name="typelibconverter-class"></a>TypeLibConverter sınıfı  
 <xref:System.Runtime.InteropServices.TypeLibConverter> Bulunan sınıfı **System.Runtime.Interop** ad alanı, sınıflar ve arabirimler COM tür kitaplığının derlemedeki bulunan dönüştürür. Bu API önceki bölümde açıklanan tür kitaplığı verici aynı tür bilgileri üretir.  
  
 **TypeLibConverter sınıfı** uygulayan <xref:System.Runtime.InteropServices.ITypeLibConverter>.  
  
<a name="cpconpackagingassemblyforcomanchor3"></a>   
## <a name="assembly-registration-tool"></a>Derleme kayıt aracı  
 [Derleme Kayıt Aracı (Regasm.exe)](../tools/regasm-exe-assembly-registration-tool.md) oluşturabilir ve, uyguladığınızda tür kitaplığının kaydı **TLB:** seçeneği. COM istemcileri tür kitaplıklarının Windows Kayıt Defteri'nde yüklü olmasını gerektirir. Bu seçenek olmadan Regasm.exe türleri yalnızca bir derleme, tür kitaplığı kaydeder. Bir derlemede türlerini kaydetme ve tür kitaplığını kaydetmede ayrı etkinliklerdir.  
  
<a name="cpconpackagingassemblyforcomanchor4"></a>   
## <a name="net-services-installation-tool"></a>.NET Hizmetleri Yükleme aracı  
 [.NET Hizmetleri Yükleme aracı (Regsvcs.exe)](../tools/regsvcs-exe-net-services-installation-tool.md) yönetilen sınıflar Windows 2000 Bileşen Hizmetleri'ne ekler ve tek bir aracı içindeki çeşitli görevleri birleştirir. Yükleme ve bir derlemeyi kaydetme ek olarak, Regsvcs.exe oluşturmak, kaydetme ve var olan bir COM + 1.0 uygulamasına tür kitaplığı yükleyin.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 <xref:System.Runtime.InteropServices.TypeLibConverter>  
 <xref:System.Runtime.InteropServices.ITypeLibConverter>  
 [.NET Framework Bileşenlerini COM'da Gösterme](exposing-dotnet-components-to-com.md)  
 [Birlikte Çalışma için .NET Türlerini Niteleme](qualifying-net-types-for-interoperation.md)  
 [Sınıf arabirimi Tanıtımı](com-callable-wrapper.md#introducing-the-class-interface)  
 [Bütünleştirilmiş Kod Güvenliği Konuları](../app-domains/assembly-security-considerations.md)  
 [Tlbexp.exe (Tür Kitaplığı Dışarı Aktarıcı)](../tools/tlbexp-exe-type-library-exporter.md)  
 [Bütünleştirilmiş Kodları COM ile Kaydetme](registering-assemblies-with-com.md)  
 [Nasıl yapılır: tür kitaplıklarını uygulamalarında Win32 kaynaklar olarak ekleme](https://msdn.microsoft.com/library/c97b4b8c-2ab7-4ac7-8fc8-0ba5c5d59c44(v=vs.100))
