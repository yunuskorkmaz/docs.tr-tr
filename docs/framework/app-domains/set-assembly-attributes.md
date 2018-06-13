---
title: Derleme Özniteliklerini Ayarlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- assemblies [.NET Framework], attributes
- assembly binding, attributes
- assembly manifest, attributes
ms.assetid: 36a98a81-b5b5-4c19-912a-11f91eff7f4e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: af1db244f02701e6da1604ec406f4fb2940f8f78
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32752208"
---
# <a name="setting-assembly-attributes"></a>Derleme Özniteliklerini Ayarlama
Derleme özniteliklerinin bir derleme hakkında bilgi sağlayan değerlerdir. Öznitelikleri bilgi aşağıdaki kümelere ayrılmıştır:  
  
-   Derleme kimlik öznitelikleri.  
  
-   Bilgilendirme öznitelikleri.  
  
-   Derleme bildirimi öznitelikleri.  
  
-   Güçlü ad öznitelikleri.  
  
## <a name="assembly-identity-attributes"></a>Derleme kimlik öznitelikleri  
 Tanımlayıcı ad (varsa), birlikte üç öznitelikleri derleme kimliğini belirlemek: ad, sürüm ve kültür. Bu öznitelikler derlemenin tam adını formunu ve kod derlemede başvurulduğunda gereklidir. Bir derlemenin sürüm ve kültür ayarlamak için öznitelikler kullanabilirsiniz. Derleyici veya [derleme bağlayıcı (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) derleme oluşturulduğunda derleme bildirimi içeren dosyasını temel alarak ad değeri ayarlar.  
  
 Aşağıdaki tabloda, sürüm ve kültür öznitelikleri açıklanmaktadır.  
  
|Derleme IDENTITY özniteliği|Açıklama|  
|---------------------------------|-----------------|  
|<xref:System.Reflection.AssemblyCultureAttribute>|Derleme destekleyen kültür gösteren numaralandırılmış alanı. Bir derlemeyi varsayılan kültür için kaynaklar içerdiği belirten kültür bağımsızlığı de belirtebilirsiniz. **Not:** çalışma kümesine kültür özniteliğine sahip herhangi bir derlemesinin değerlendirir uydu derlemesi olarak null. Bu tür derlemeler uydu derleme bağlama tabi kurallardır. Daha fazla bilgi için bkz: [nasıl çalışma zamanı bulur derlemeleri](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).|  
|<xref:System.Reflection.AssemblyFlagsAttribute>|Derleme özniteliklerinin, derleme yan yana çalıştırılabileceği olup olmadığı gibi ayarlar değeri.|  
|<xref:System.Reflection.AssemblyVersionAttribute>|Sayısal değer biçimde *ana*. *küçük*. *Yapı*. *Düzeltme* (örneğin, 2.4.0.0). Ortak dil çalışma zamanı tanımlayıcı adlı derlemeler Bağlama işlemleri gerçekleştirmek için bu değeri kullanır. **Not:** varsa <xref:System.Reflection.AssemblyInformationalVersionAttribute> özniteliği bir derlemeye uygulanmaz tarafından belirtilen sürüm numarası <xref:System.Reflection.AssemblyVersionAttribute> özniteliği tarafından kullanılan <xref:System.Windows.Forms.Application.ProductVersion%2A?displayProperty=nameWithType>, <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType>, ve <xref:System.Windows.Forms.Application.UserAppDataRegistry%2A?displayProperty=nameWithType> özellikleri.|  
  
 Aşağıdaki kod örneği sürümü ve kültür öznitelikleri bir derlemeye uygulanır gösterilmektedir.  
  
 [!code-cpp[AssemblyDelaySignAttribute#3](../../../samples/snippets/cpp/VS_Snippets_CLR/AssemblyDelaySignAttribute/cpp/source2.cpp#3)]
 [!code-csharp[AssemblyDelaySignAttribute#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AssemblyDelaySignAttribute/cs/source2.cs#3)]
 [!code-vb[AssemblyDelaySignAttribute#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AssemblyDelaySignAttribute/vb/source2.vb#3)]  
  
## <a name="informational-attributes"></a>Bilgilendirme öznitelikleri  
 Bilgilendirme öznitelikleri, ek şirket veya bir derleme için ürün bilgi sağlamak için kullanabilirsiniz. Aşağıdaki tabloda bir derlemeye uygulayabilirsiniz bilgilendirme öznitelikleri açıklanmaktadır.  
  
|Bilgilendirme özniteliği|Açıklama|  
|-----------------------------|-----------------|  
|<xref:System.Reflection.AssemblyCompanyAttribute>|Bir şirket adı belirterek dize değeri.|  
|<xref:System.Reflection.AssemblyCopyrightAttribute>|Telif hakkı bilgileri belirten değeri dize.|  
|<xref:System.Reflection.AssemblyFileVersionAttribute>|Win32 dosya sürüm numarası belirten dize değeri. Bu normalde derleme sürümü varsayılan olarak.|  
|<xref:System.Reflection.AssemblyInformationalVersionAttribute>|Dize değeri bir tam ürün sürüm numarası gibi ortak dil çalışma zamanı tarafından kullanılmaz sürüm bilgilerini belirtme. **Not:** bu öznitelik bir derlemeye uyguladıysanız, belirtir dize çalışma zamanında kullanarak elde edilebilir <xref:System.Windows.Forms.Application.ProductVersion%2A?displayProperty=nameWithType> özelliği. Dize ayrıca tarafından sağlanan yol ve kayıt defteri anahtarı kullanılır <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType> ve <xref:System.Windows.Forms.Application.UserAppDataRegistry%2A?displayProperty=nameWithType> özellikleri.|  
|<xref:System.Reflection.AssemblyProductAttribute>|Ürün bilgisi belirten değeri dize.|  
|<xref:System.Reflection.AssemblyTrademarkAttribute>|Dize değeri ticari marka bilgileri belirtme.|  
  
 Bu öznitelikler derleme Windows özellikleri sayfasında bulunabilir veya kullanarak kılınabilir **/win32res** derleyici seçeneği kendi Win32 kaynak dosyasını belirtin.  
  
## <a name="assembly-manifest-attributes"></a>Derleme bildirimi öznitelikleri  
 Derleme bildirimi özniteliklerinin başlık, açıklama, varsayılan diğer ad ve yapılandırma dahil olmak üzere derleme bildirimi bilgi sağlamak için kullanabilirsiniz. Aşağıdaki tabloda derleme bildirimi öznitelikleri açıklanmaktadır.  
  
|Derleme bildirimi özniteliği|Açıklama|  
|---------------------------------|-----------------|  
|<xref:System.Reflection.AssemblyConfigurationAttribute>|Tekil veya hata ayıklama gibi derleme yapılandırmasını gösteren değeri dize. Çalışma zamanı bu değeri kullanmaz.|  
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|Derlemelere başvurma tarafından kullanılacak varsayılan diğer belirten dize değeri. Derlemenin adını (bir GUID değeri gibi) kolay olmadığında bu değer kolay bir ad sağlar. Bu değer, tam derleme adının kısa form olarak da kullanılabilir.|  
|<xref:System.Reflection.AssemblyDescriptionAttribute>|Dize değeri yapısı ve derleme amacı özetler kısa bir açıklama belirtme.|  
|<xref:System.Reflection.AssemblyTitleAttribute>|Derleme için bir kolay ad belirten dize değeri. Örneğin, comdlg adlı bir derleme Microsoft ortak iletişim kutusu denetimi başlığı olabilir.|  
  
## <a name="strong-name-attributes"></a>Güçlü ad öznitelikleri  
 Güçlü ad öznitelikleri, derleme için güçlü bir ad ayarlamak için kullanabilirsiniz. Aşağıdaki tabloda, güçlü ad öznitelikleri açıklanmaktadır.  
  
|Güçlü ad öznitelikleri|Açıklama|  
|----------------------------|-----------------|  
|<xref:System.Reflection.AssemblyDelaySignAttribute>|Gecikmeli imzalama kullanılmakta olduğunu gösteren Boole değeri.|  
|<xref:System.Reflection.AssemblyKeyFileAttribute>|Ortak anahtar (Gecikmeli imzalama kullanarak) varsa, dosya veya ortak ve özel anahtarlar adını belirten dize değeri bir parametre olarak bu öznitelik oluşturucuya geçirilen. Dosya adı çıkış dosyası yoluyla göreli (.exe veya .dll), kaynak dosya yolu olmadığını unutmayın.|  
|<xref:System.Reflection.AssemblyKeyNameAttribute>|Bu öznitelik oluşturucuya parametre olarak geçirilen anahtar çiftini içeren anahtar kapsayıcı gösterir.|  
  
 Aşağıdaki kod örneğinde tanımlayıcı adlı bir derleme ortak bir anahtar dosyası oluşturmak imzalamayı geciktirme kullanarak çağrıldığında uygulamak için öznitelikleri gösterir `myKey.snk`.  
  
 [!code-cpp[AssemblyDelaySignAttribute#4](../../../samples/snippets/cpp/VS_Snippets_CLR/AssemblyDelaySignAttribute/cpp/source2.cpp#4)]
 [!code-csharp[AssemblyDelaySignAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AssemblyDelaySignAttribute/cs/source2.cs#4)]
 [!code-vb[AssemblyDelaySignAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AssemblyDelaySignAttribute/vb/source2.vb#4)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bütünleştirilmiş Kodlar Oluşturma](../../../docs/framework/app-domains/create-assemblies.md)  
 [Bütünleştirilmiş Kodlarla Programlama](../../../docs/framework/app-domains/programming-with-assemblies.md)
