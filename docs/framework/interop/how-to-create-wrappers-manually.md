---
title: 'Nasıl yapılır: Sarmalayıcıları Elle Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- wrappers, creating manually
ms.assetid: cc2a70d8-6a58-4071-a8cf-ce28c018c09b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2d6959ac8b2315d928ab2ac362bb3b2c4081d46e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59117111"
---
# <a name="how-to-create-wrappers-manually"></a>Nasıl yapılır: Sarmalayıcıları Elle Oluşturma
El ile yönetilen kaynak kodda COM türlerini bildirmek karar verirseniz, başlatmak için en iyi varolan arabirim tanımlama dili (IDL) dosya veya tür kitaplığı ile yerdir. IDL dosyası yok veya bir tür kitaplığı dosyası oluşturulamıyor, yönetilen bildirimleri oluşturarak COM türlerini benzetimi yapabilir ve elde edilen derlemeyi bir tür kitaplığına dışarı aktarma.  
  
### <a name="to-simulate-com-types-from-managed-source"></a>COM benzetimini yapmak için yönetilen kaynak türleri  
  
1.  Ortak dil belirtimi (CLS) ile uyumlu bir dil alanlarında türleri bildirin ve dosyasını derleyin.  
  
2.  Verme türleriyle içeren derlemenin [tür kitaplığı dışarı Aktarıcı (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md).  
  
3.  Dışarı aktarılan COM türü kitaplık yönetilen türler COM odaklı bildirmek için temel olarak kullanın.  
  
### <a name="to-create-a-runtime-callable-wrapper-rcw"></a>Bir çalışma zamanı çağrılabilir sarmalayıcı (RCW) oluşturmak için  
  
1.  Bir IDL dosyası veya tür kitaplığı dosyası sahip olduğunuz varsayılarak, hangi sınıfları ve arabirimleri özel RCW dahil etmek istediğiniz karar verin. Doğrudan veya dolaylı olarak kullanmak için uygulamanızı düşünmüyorsanız herhangi bir türü hariç tutabilirsiniz.  
  
2.  CLS uyumlu bir dilde kaynak dosyası oluşturma ve türlerini bildirir. Bkz: [tür kitaplığını derlemeye dönüştürme özeti](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100)) içeri aktarma dönüştürme işlemi için eksiksiz bir açıklaması için. Özel RCW oluşturduğunuzda, etkili bir şekilde el ile tarafından sağlanan türü dönüştürme etkinliği gerçekleştirdiğiniz [tür kitaplığı alma programı (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md). Sonraki bölümde örnek bir IDL veya tür kitaplığı dosyası ve bunların karşılık gelen türler türlerini gösterir. C# kod.  
  
3.  Bildirimleri tamamlandığında, herhangi bir yönetilen kaynak kod derleme gibi dosyasını derleyin.  
  
4.  Tlbimp.exe ile içeri türlerine sahip olarak, bazı doğrudan kodunuza ekleyebilirsiniz. ek bilgi gerektirir. Ayrıntılar için bkz [nasıl yapılır: Birlikte çalışma derlemelerini düzenleme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8zbc969t(v=vs.100)).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği gösterilmektedir `ISATest` arabirimi ve `SATest` sınıfı IDL ve karşılık gelen türler C# kaynak kodu.  
  
 **IDL veya tür kitaplığı dosyası**  
  
```  
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
  
 **Yönetilen kaynak kodundaki sarmalayıcı**  
  
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

- [Çalışma Zamanı Aranabilir Sarmalayıcılarını Özelleştirme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100))
- [COM Veri Türleri](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sak564ww(v=vs.100))
- [Nasıl yapılır: Birlikte çalışma derlemelerini düzenleme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8zbc969t(v=vs.100))
- [Tür Kitaplığından Derlemeye Dönüştürme Özeti](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))
- [Tlbimp.exe (Tür Kitaplığı İçeri Aktarıcı)](../tools/tlbimp-exe-type-library-importer.md)
- [Tlbexp.exe (Tür Kitaplığı Dışarı Aktarıcı)](../tools/tlbexp-exe-type-library-exporter.md)
