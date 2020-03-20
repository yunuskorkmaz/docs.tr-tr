---
title: 'Nasıl yapılır: Sarmalayıcıları Elle Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- wrappers, creating manually
ms.assetid: cc2a70d8-6a58-4071-a8cf-ce28c018c09b
ms.openlocfilehash: a7818a1c08d8538acfacb22dc270d7ef23a7a582
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181424"
---
# <a name="how-to-create-wrappers-manually"></a>Nasıl yapılır: Sarmalayıcıları Elle Oluşturma
Yönetilen kaynak kodunda COM türlerini el ile bildirmeye karar verirseniz, başlamak için en iyi yer varolan bir Arabirim Tanımı Dili (IDL) dosyası veya tür kitaplığıdır. IDL dosyasıyoksa veya bir tür kitaplığı dosyası oluşturamıyorsa, yönetilen bildirimler oluşturarak ve ortaya çıkan derlemeyi bir tür kitaplığına dışa aktararak COM türlerini simüle edebilirsiniz.  
  
### <a name="to-simulate-com-types-from-managed-source"></a>Yönetilen kaynaktan COM türlerini simüle etmek için  
  
1. Türleri Ortak Dil Belirtimi (CLS) ile uyumlu bir dilde bildirin ve dosyayı derle.  
  
2. [Tip Kitaplığı İhracatçısı (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md)ile türleri içeren montajı dışa aktarın.  
  
3. Dışa aktarılan COM türü kitaplığını, COM yönelimli yönetilen türleri bildirmek için temel olarak kullanın.  
  
### <a name="to-create-a-runtime-callable-wrapper-rcw"></a>Çalışma zamanı çağrılabilir sarıcı (RCW) oluşturmak için  
  
1. Bir IDL dosyanız veya tür kitaplığı dosyanız olduğunu varsayarsak, özel RCW'ye hangi sınıfları ve arabirimleri eklemek istediğinize karar verin. Doğrudan veya dolaylı olarak uygulamanızda kullanmak niyetinde olmadığınız türleri hariç tutabilirsiniz.  
  
2. CLS uyumlu bir dilde bir kaynak dosyası oluşturun ve türleri bildirin. Alma dönüştürme işleminin tam açıklaması için [Derleme Dönüşüm Özeti türüne](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100)) bakın. Etkili bir şekilde, özel bir RCW oluşturduğunuzda, [Tür Kitaplığı İthalatçısı (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md)tarafından sağlanan tür dönüştürme etkinliğini el ile gerçekleştirirsiniz. Sonraki bölümdeki örnekte, IDL veya tür kitaplığı dosyasındaki türleri ve bunların C# kodundaki karşılık gelen türleri gösterilmektedir.  
  
3. Bildirimler tamamlandığında, diğer yönetilen kaynak kodlarını derlerken dosyayı derle.  
  
4. Tlbimp.exe ile alınan türleri olduğu gibi, bazı doğrudan kodunuza ekleyebilirsiniz ek bilgi gerektirir. Ayrıntılar için [bkz: Interop Montajlarını Edit.](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8zbc969t(v=vs.100))  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, IDL'deki `ISATest` `SATest` arabirim ve sınıfın bir örneğini ve C# kaynak kodundaki ilgili türleri gösterir.  
  
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
  
 **Yönetilen kaynak kodunda sarıcı**  
  
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

- [Runtime Çağrılanabilir Sarmalayıcıları Özelleştirme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100))
- [COM Veri Türleri](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sak564ww(v=vs.100))
- [Nasıl yapılsın: Interop Montajlarını Edit](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8zbc969t(v=vs.100))
- [Tür Kitaplığı ndan Montaja Dönüşüm Özeti](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))
- [Tlbimp.exe (Tür Kitaplığı İçeri Aktarıcı)](../tools/tlbimp-exe-type-library-importer.md)
- [Tlbexp.exe (Tür Kitaplığı Dışarı Aktarıcı)](../tools/tlbexp-exe-type-library-exporter.md)
