---
title: 'Nasıl yapılır: Sarmalayıcıları Elle Oluşturma'
description: COM türlerinin sarmalayıcılarını el ile oluşturun. Mevcut bir IDL dosyası veya tür kitaplığı kullanın ya da yönetilen bildirimler oluşturun ve derlemeyi bir tür kitaplığına dışarı aktarın.
ms.date: 03/30/2017
helpviewer_keywords:
- wrappers, creating manually
ms.assetid: cc2a70d8-6a58-4071-a8cf-ce28c018c09b
ms.openlocfilehash: 0d696adbe1ee224e78f79a049ed2e41d50be1faa
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554175"
---
# <a name="how-to-create-wrappers-manually"></a>Nasıl yapılır: Sarmalayıcıları Elle Oluşturma
COM türlerini yönetilen kaynak kodunda el ile bildirmeye karar verirseniz, başlamak için en iyi yer, var olan bir arabirim tanım dili (IDL) dosyası veya tür kitaplığı vardır. IDL dosyanız yoksa veya bir tür kitaplığı dosyası üretüriyorsa, yönetilen bildirimler oluşturarak ve ortaya çıkan derlemeyi bir tür kitaplığına vererek COM türlerinin benzetimini yapabilirsiniz.  
  
### <a name="to-simulate-com-types-from-managed-source"></a>Yönetilen kaynaktan COM türlerinin benzetimini yapmak için  
  
1. Türleri ortak dil belirtimi (CLS) ile uyumlu bir dilde bildirin ve dosyayı derleyin.  
  
2. Türleri içeren derlemeyi [tür kitaplığı verme programı (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md)ile dışarı aktarın.  
  
3. COM tabanlı yönetilen türler bildirmek için bir temel olarak, dışarıya aktarılmış COM tür kitaplığını kullanın.  
  
### <a name="to-create-a-runtime-callable-wrapper-rcw"></a>Çalışma zamanında çağrılabilir sarmalayıcı (RCW) oluşturmak için  
  
1. Bir IDL dosyası ya da tür kitaplığı dosyanız olduğunu varsayarsak, özel RCW 'ya dahil etmek istediğiniz sınıfları ve arabirimleri belirleyin. Uygulamanızda doğrudan veya dolaylı olarak kullanmayı planlamadığınız tüm türleri dışarıda bırakabilirsiniz.  
  
2. CLS uyumlu bir dilde kaynak dosyası oluşturun ve türleri bildirin. İçeri aktarma dönüştürme işleminin tüm açıklaması için bkz. [tür kitaplığı, derleme dönüştürme Özeti](/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100)) . Etkin olarak, özel bir RCW oluşturduğunuzda, [tür kitaplığı alma programı (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md)tarafından sağlanmış tür dönüştürme etkinliğini el ile gerçekleştirmekten olursunuz. Sonraki bölümdeki örnekte, bir IDL veya tür kitaplığı dosyasındaki türler ve C# kodunda bunlara karşılık gelen türler gösterilmektedir.  
  
3. Bildirimler tamamlandığında, başka bir yönetilen kaynak kodu derlerken dosyayı derleyin.  
  
4. Tlbimp.exe ile içeri aktarılan türlerde, bazıları doğrudan kodunuza ekleyebileceğiniz ek bilgiler gerektirir. Ayrıntılar için bkz. [nasıl yapılır: birlikte çalışma derlemelerini düzenleme](/previous-versions/dotnet/netframework-4.0/8zbc969t(v=vs.100)).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, `ISATest` `SATest` IDL 'deki arabirime ve sınıfa ve C# kaynak kodundaki karşılık gelen türlere bir örnek gösterir.  
  
 **IDL veya tür kitaplığı dosyası**  
  
```cpp
 [  
object,  
uuid(40A8C65D-2448-447A-B786-64682CBEF133),  
dual,  
helpstring("ISATest Interface"),  
pointer_default(unique)  
 ]  
interface ISATest : IDispatch  
 {  
[id(1), helpstring("method InSArray")]
HRESULT InSArray([in] SAFEARRAY(int) *ppsa, [out,retval] int *pSum);  
 };  
 [  
uuid(116CCA1E-7E39-4515-9849-90790DA6431E),  
helpstring("SATest Class")  
 ]  
coclass SATest  
 {  
  [default] interface ISATest;  
 };  
```  
  
 **Yönetilen kaynak kodunda sarmalayıcı**  
  
```csharp  
using System;  
using System.Runtime.InteropServices;  
using System.Runtime.CompilerServices;  
  
[assembly:Guid("E4A992B8-6F5C-442C-96E7-C4778924C753")]  
[assembly:ImportedFromTypeLib("SAServerLib")]  
namespace SAServer  
{  
 [ComImport]  
 [Guid("40A8C65D-2448-447A-B786-64682CBEF133")]  
 [TypeLibType(TypeLibTypeFlags.FLicensed)]  
 public interface ISATest  
 {  
  [DispId(1)]  
  //[MethodImpl(MethodImplOptions.InternalCall,  
  // MethodCodeType=MethodCodeType.Runtime)]  
  int InSArray( [MarshalAs(UnmanagedType.SafeArray,  
      SafeArraySubType=VarEnum.VT_I4)] ref int[] param );  
 }
 [ComImport]  
 [Guid("116CCA1E-7E39-4515-9849-90790DA6431E")]  
 [ClassInterface(ClassInterfaceType.None)]  
 [TypeLibType(TypeLibTypeFlags.FCanCreate)]  
 public class SATest : ISATest  
 {  
  [DispId(1)]  
  [MethodImpl(MethodImplOptions.InternalCall,
  MethodCodeType=MethodCodeType.Runtime)]  
  extern int ISATest.InSArray( [MarshalAs(UnmanagedType.SafeArray,
  SafeArraySubType=VarEnum.VT_I4)] ref int[] param );  
 }  
}  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma zamanı çağrılabilir sarmalayıcıları özelleştirme](/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100))
- [COM veri türleri](/previous-versions/dotnet/netframework-4.0/sak564ww(v=vs.100))
- [Nasıl yapılır: birlikte çalışma derlemelerini düzenleme](/previous-versions/dotnet/netframework-4.0/8zbc969t(v=vs.100))
- [Tür kitaplığını derlemeye dönüştürme Özeti](/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))
- [Tlbimp.exe (tür kitaplığı Içeri Aktarıcı)](../tools/tlbimp-exe-type-library-importer.md)
- [Tlbexp.exe (tür kitaplığı verme programı)](../tools/tlbexp-exe-type-library-exporter.md)
