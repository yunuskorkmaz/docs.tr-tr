---
title: "Nasıl yapılır: Sarmalayıcıları Elle Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- wrappers, creating manually
ms.assetid: cc2a70d8-6a58-4071-a8cf-ce28c018c09b
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7ac7afdd85037d50bdda9fae0a33896dc441bce5
ms.sourcegitcommit: 1c0b0f082b3f300e54b4d069b317ac724c88ddc3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2018
---
# <a name="how-to-create-wrappers-manually"></a>Nasıl yapılır: Sarmalayıcıları Elle Oluşturma
Yönetilen kaynak kodunda el ile COM türlerinizi karar verirseniz, başlatmak için en iyi varolan arabirimi tanım dili (IDL) dosyası ya da tür kitaplığı ile yerdir. IDL dosya yok veya bir tür kitaplığı dosya oluşturulamıyor, yönetilen bildirimleri oluşturarak COM türlerini benzetimini yapabilirsiniz ve sonuçta elde edilen derleme için bir tür kitaplığı dışarı aktarma.  
  
### <a name="to-simulate-com-types-from-managed-source"></a>Yönetilen kaynak COM türlerinden benzetimini yapmak için  
  
1.  Ortak dil belirtimi (CLS) ile uyumlu olan bir dildeki türleri bildirme ve dosyasını derleyin.  
  
2.  Türleriyle içeren derlemenin verme [tür kitaplığı dışarı Aktarıcı (Tlbexp.exe)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md).  
  
3.  Dışarı aktarılan COM tür kitaplığı yönetilen türleri COM odaklı bildirmek için temel olarak kullanın.  
  
### <a name="to-create-a-runtime-callable-wrapper-rcw"></a>Bir çalışma zamanı aranabilir sarmalayıcısı (RCW) oluşturmak için  
  
1.  Bir IDL dosya veya türü kitaplık dosyası olmadığı varsayılarak, hangi sınıflar ve arabirimler özel RCW dahil etmek istediğiniz karar verin. Doğrudan veya dolaylı olarak kullanmak için uygulamanızda düşünmüyorsanız türlerini hariç tutabilirsiniz.  
  
2.  CLS uyumlu bir dilde kaynak dosyası oluşturma ve türleri bildirin. Bkz: [derleme dönüştürme özeti için tür kitaplığı](http://msdn.microsoft.com/library/bf3f90c5-4770-4ab8-895c-3ba1055cc958) alma dönüştürme işlemini eksiksiz bir açıklaması. Özel RCW oluşturduğunuzda, etkili bir şekilde el ile tarafından sağlanan tür dönüştürme etkinliği gerçekleştirdiğiniz [tür kitaplığı içeri Aktarıcı (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md). Sonraki bölümdeki örnek, bir IDL veya tür kitaplığı dosyasını ve bunların karşılık gelen türlerine C# kodunda türlerini gösterir.  
  
3.  Bildirimleri tamamlandığı zaman, herhangi bir yönetilen kaynak kodu derleme gibi dosyasını derleyin.  
  
4.  Türleriyle Tlbimp.exe ile içeri gibi bazı kodunuzu doğrudan ekleyebileceğiniz ek bilgi gerektirir. Ayrıntılar için bkz [nasıl yapılır: Düzenle birlikte çalışma derlemeleri](https://msdn.microsoft.com/library/16aacb20-2269-42bf-a812-b6a7df17e277(v=vs.100)).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği gösterilmektedir `ISATest` arabirimi ve `SATest` IDL sınıfında ve karşılık gelen türlerine C# kaynak kodu.  
  
 **IDL veya türü kitaplık dosyası**  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çalışma zamanı aranabilir sarmalayıcıları özelleştirme](http://msdn.microsoft.com/library/4652beaf-77d0-4f37-9687-ca193288c0be)  
 [COM veri türleri](http://msdn.microsoft.com/library/f93ae35d-a416-4218-8700-c8218cc90061)  
 [Nasıl yapılır: Düzenle birlikte çalışma derlemeleri](http://msdn.microsoft.com/library/16aacb20-2269-42bf-a812-b6a7df17e277)  
 [Derleme dönüştürme özeti için tür kitaplığı](http://msdn.microsoft.com/library/bf3f90c5-4770-4ab8-895c-3ba1055cc958)  
 [Tlbimp.exe (Tür Kitaplığı İçeri Aktarıcı)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md)  
 [Tlbexp.exe (Tür Kitaplığı Dışarı Aktarıcı)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md)
