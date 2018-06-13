---
title: 'Nasıl yapılır: Derleme İçeriklerini Görüntüleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- assembly manifest, viewing information
- Ildasm.exe
- MSIL Disassembler
- assemblies [.NET Framework], viewing contents
- viewing assembly information
- MSIL
- viewing MSIL information
ms.assetid: fb7baaab-4c0d-47ad-8fd3-4591cf834709
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eadc320483d46503e7331ef57b0cc29b08f13f4c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32742841"
---
# <a name="how-to-view-assembly-contents"></a>Nasıl yapılır: Derleme İçeriklerini Görüntüleme
Kullanabileceğiniz [Ildasm.exe (IL ayrıştırıcı)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) bir dosyada Microsoft Ara dili (MSIL) bilgilerini görüntülemek için. İncelenmesi dosyanın derleme olup, bu bilgileri derlemenin öznitelikleri yanı sıra diğer modüller ve derleme başvurularını ekleyebilirsiniz. Bu bilgiler bir dosyayı bir derleme veya derleme parçası olmasına ve dosya derlemeleri veya diğer modüller başvurular olup saptamanıza yardımcı olabilir.  
  
### <a name="to-display-the-contents-of-an-assembly-using-ildasmexe"></a>Ildasm.exe kullanarak bir derlemeye içeriğini görüntülemek için  
  
1.  Tür **ildasm** \< *derleme adı*> komut isteminde. Örneğin, aşağıdaki komutu ayrıştırır `Hello.exe` derleme.  
  
    ```  
    ildasm Hello.exe  
    ```  
  
### <a name="to-view-assembly-manifest-information"></a>Derleme bildirimi bilgilerini görüntülemek için  
  
1.  MSIL ayrıştırıcı penceresinde bildirim simgesini çift tıklatın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, temel bir "Hello, World" programla başlatır. Program derledikten sonra Ildasm.exe Hello.exe derleme Ayır ve derleme bildirimi görüntülemek için kullanın.  
  
 [!code-cpp[Conceptual.Assembly.Contents#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.contents/cpp/source.cpp#1)]
 [!code-csharp[Conceptual.Assembly.Contents#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.contents/cs/source.cs#1)]
 [!code-vb[Conceptual.Assembly.Contents#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.contents/vb/source.vb#1)]  
  
 Komut ildasm.exe Hello.exe derleme üzerinde çalışan ve IL DASM penceresinde bildirim simgesini çift şu çıkışı üretir:  
  
```  
// Metadata version: v4.0.30319  
.assembly extern mscorlib  
{  
  .publickeytoken = (B7 7A 5C 56 19 34 E0 89 )                         // .z\V.4..  
  .ver 4:0:0:0  
}  
.assembly Hello  
{  
  .custom instance void [mscorlib]System.Runtime.CompilerServices.CompilationRelaxationsAttribute::.ctor(int32) = ( 01 00 08 00 00 00 00 00 )   
  .custom instance void [mscorlib]System.Runtime.CompilerServices.RuntimeCompatibilityAttribute::.ctor() = ( 01 00 01 00 54 02 16 57 72 61 70 4E 6F 6E 45 78   // ....T..WrapNonEx  
                                                                                                             63 65 70 74 69 6F 6E 54 68 72 6F 77 73 01 )       // ceptionThrows.  
  .hash algorithm 0x00008004  
  .ver 0:0:0:0  
}  
.module Hello.exe  
// MVID: {7C2770DB-1594-438D-BAE5-98764C39CCCA}  
.imagebase 0x00400000  
.file alignment 0x00000200  
.stackreserve 0x00100000  
.subsystem 0x0003       // WINDOWS_CUI  
.corflags 0x00000001    //  ILONLY  
// Image base: 0x00600000  
```  
  
 Aşağıdaki tabloda, her örnekte kullanılan Hello.exe derlemenin derleme bildirimi yönergesinde açıklanmaktadır.  
  
|Yönergesi|Açıklama|  
|---------------|-----------------|  
|**.Assembly extern \<**  *derleme adı* **>**|Geçerli bir modül tarafından başvurulan öğeleri içeren başka bir derleme belirtir (Bu örnekte, `mscorlib`).|  
|**.PublicKeyToken \<**  *belirteci* **>**|Başvurulan derlemeyi gerçek anahtarı belirteci belirtir.|  
|**.ver \<**  *sürüm numarası* **>**|Başvurulan derlemeyi sürüm numarasını belirtir.|  
|**.Assembly \<**  *derleme adı* **>**|Derleme adı belirtir.|  
|**.hash algoritması \<**  *Int32 değeri* **>**|Kullanılan karma algoritmasını belirtir.|  
|**.ver \<**  *sürüm numarası* **>**|Derlemenin sürüm numarasını belirtir.|  
|**.Module \<**  *dosya adı* **>**|Derlemeyi oluşturan modüllerin adını belirtir. Bu örnekte, yalnızca bir dosyasından derleme oluşur.|  
|**.Subsystem \<**  *değeri* **>**|Program için gereken uygulama ortamı belirtir. Bu örnekte, bu yürütülebilir dosya bir konsoldan çalıştırıldığını 3 değeri gösterir.|  
|**.corflags**|Şu anda ayrılmış alan meta veriler.|  
  
 Derleme bildirimi derleme içeriğini bağlı olarak farklı yönergeleri sayısı içerebilir. Derleme bildirimi yönergeleri kapsamlı bir listesi için "özellikle Bölüm II: meta veri tanım ve semantik" ve "Bölüm III: CIL yönerge kümesi" ECMA belgelerine bakın. Belge çevrimiçi kullanılabilir; bkz: [ECMA C# ve ortak dil altyapısı standartları](http://go.microsoft.com/fwlink/?LinkID=99212) MSDN'de ve [standart ECMA-335 - ortak dil altyapısı (CLI)](http://go.microsoft.com/fwlink/?LinkID=65552) Ecma uluslararası Web sitesinde.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Uygulama Etki Alanları ve Derlemeler](http://msdn.microsoft.com/library/433b04ae-4ba8-4849-9dbd-79194f240346)  
 [Uygulama Etki Alanları ve Bütünleştirilmiş Kodlar için Nasıl Yapılır Konuları](../../../docs/framework/app-domains/application-domains-and-assemblies-how-to-topics.md)  
 [Ildasm.exe (IL Ayrıştırıcı)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md)
