---
title: 'Nasıl yapılır: Sarmalayıcıları elle oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- wrappers, creating manually
ms.assetid: cc2a70d8-6a58-4071-a8cf-ce28c018c09b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fba0de3f45afc199255dce93e69142724b68b0fd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54553041"
---
# <a name="how-to-create-wrappers-manually"></a>Nasıl yapılır: Sarmalayıcıları elle oluşturma
El ile yönetilen kaynak kodda COM türlerini bildirmek karar verirseniz, başlatmak için en iyi varolan arabirim tanımlama dili (IDL) dosya veya tür kitaplığı ile yerdir. IDL dosyası yok veya bir tür kitaplığı dosyası oluşturulamıyor, yönetilen bildirimleri oluşturarak COM türlerini benzetimi yapabilir ve elde edilen derlemeyi bir tür kitaplığına dışarı aktarma.  
  
### <a name="to-simulate-com-types-from-managed-source"></a>COM benzetimini yapmak için yönetilen kaynak türleri  
  
1.  Ortak dil belirtimi (CLS) ile uyumlu bir dil alanlarında türleri bildirin ve dosyasını derleyin.  
  
2.  Verme türleriyle içeren derlemenin [tür kitaplığı dışarı Aktarıcı (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md).  
  
3.  Dışarı aktarılan COM türü kitaplık yönetilen türler COM odaklı bildirmek için temel olarak kullanın.  
  
### <a name="to-create-a-runtime-callable-wrapper-rcw"></a>Bir çalışma zamanı çağrılabilir sarmalayıcı (RCW) oluşturmak için  
  
1.  Bir IDL dosyası veya tür kitaplığı dosyası sahip olduğunuz varsayılarak, hangi sınıfları ve arabirimleri özel RCW dahil etmek istediğiniz karar verin. Doğrudan veya dolaylı olarak kullanmak için uygulamanızı düşünmüyorsanız herhangi bir türü hariç tutabilirsiniz.  
  
2.  CLS uyumlu bir dilde kaynak dosyası oluşturma ve türlerini bildirir. Bkz: [tür kitaplığını derlemeye dönüştürme özeti](https://msdn.microsoft.com/library/bf3f90c5-4770-4ab8-895c-3ba1055cc958(v=vs.100)) içeri aktarma dönüştürme işlemi için eksiksiz bir açıklaması için. Özel RCW oluşturduğunuzda, etkili bir şekilde el ile tarafından sağlanan türü dönüştürme etkinliği gerçekleştirdiğiniz [tür kitaplığı alma programı (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md). Sonraki bölümde örnek bir IDL veya tür kitaplığı dosyası ve bunların karşılık gelen türler türlerini gösterir. C# kod.  
  
3.  Bildirimleri tamamlandığında, herhangi bir yönetilen kaynak kod derleme gibi dosyasını derleyin.  
  
4.  Tlbimp.exe ile içeri türlerine sahip olarak, bazı doğrudan kodunuza ekleyebilirsiniz. ek bilgi gerektirir. Ayrıntılar için bkz [nasıl yapılır: Birlikte çalışma derlemelerini düzenleme](https://msdn.microsoft.com/library/16aacb20-2269-42bf-a812-b6a7df17e277(v=vs.100)).  
  
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
- [Çalışma zamanı aranabilir sarmalayıcılarını özelleştirme](https://msdn.microsoft.com/library/4652beaf-77d0-4f37-9687-ca193288c0be(v=vs.100))
- [COM veri türleri](https://msdn.microsoft.com/library/f93ae35d-a416-4218-8700-c8218cc90061(v=vs.100))
- [Nasıl yapılır: Birlikte çalışma derlemelerini düzenleme](https://msdn.microsoft.com/library/16aacb20-2269-42bf-a812-b6a7df17e277(v=vs.100))
- [Tür kitaplığını derlemeye dönüştürme özeti](https://msdn.microsoft.com/library/bf3f90c5-4770-4ab8-895c-3ba1055cc958(v=vs.100))
- [Tlbimp.exe (Tür Kitaplığı İçeri Aktarıcı)](../tools/tlbimp-exe-type-library-importer.md)
- [Tlbexp.exe (Tür Kitaplığı Dışarı Aktarıcı)](../tools/tlbexp-exe-type-library-exporter.md)
