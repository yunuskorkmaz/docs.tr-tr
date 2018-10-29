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
ms.openlocfilehash: e1ed022193b4896f91f1096a0bb16c21f5374868
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2018
ms.locfileid: "50201432"
---
# <a name="setting-assembly-attributes"></a>Derleme Özniteliklerini Ayarlama
Derleme özniteliklerinin bir derlemeyle ilgili bilgi sağlayan değerlerdir. Öznitelik bilgileri aşağıdaki kümelere ayrılmıştır:  
  
-   Derleme kimliği öznitelikleri.  
  
-   Bilgilendirme özniteliklerini.  
  
-   Derleme bildirimi öznitelikleri.  
  
-   Tanımlayıcı ad öznitelikleri.  
  
## <a name="assembly-identity-attributes"></a>Derleme kimliği öznitelikleri  
 Tanımlayıcı bir ada (varsa) ile birlikte üç özniteliği bir derlemenin kimliğini belirlemek: ad, sürüm ve kültür. Bu öznitelikler, bütünleştirilmiş kodun tam adı oluşturur ve kodu derlemesinde başvururken kullanılır. Öznitelik, bir derlemenin sürüm ve kültür ayarlamak için kullanabilirsiniz. Derleyicinin veya [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) derleme oluşturulduğunda derleme bildirimini içeren dosyayı temel alan adı değeri ayarlar.  
  
 Aşağıdaki tabloda, sürüm ve kültür özniteliklerini açıklar.  
  
|Derleme IDENTITY özniteliği|Açıklama|  
|---------------------------------|-----------------|  
|<xref:System.Reflection.AssemblyCultureAttribute>|Derlemenin desteklediği kültür belirten numaralandırılmış alan. Bir derleme, kaynaklar için varsayılan kültürü içerdiğini gösteren kültür bağımsızlığı de belirtebilirsiniz. **Not:** kümesine kültür özniteliğine sahip herhangi bir derleme çalışma zamanı değerlendirir bir uydu derleme olarak null. Bu tür derlemeler uydu derleme bağlama tabi kurallardır. Daha fazla bilgi için [çalışma zamanı derlemeleri nasıl konumlandırır](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).|  
|<xref:System.Reflection.AssemblyFlagsAttribute>|Derleme olup yan yana çalıştırılabilir gibi derleme özniteliklerinin, ayarlar değeri.|  
|<xref:System.Reflection.AssemblyVersionAttribute>|Biçimindeki sayısal değeri *ana*. *küçük*. *derleme*. *Düzeltme* (örneğin, 2.4.0.0). Ortak dil çalışma zamanı, tanımlayıcı adlı derlemeler Bağlama işlemleri gerçekleştirmek için bu değeri kullanır. **Not:** varsa <xref:System.Reflection.AssemblyInformationalVersionAttribute> özniteliği bir derlemeye uygulanmaz tarafından belirtilen sürüm numarası <xref:System.Reflection.AssemblyVersionAttribute> özniteliği tarafından kullanılan <xref:System.Windows.Forms.Application.ProductVersion%2A?displayProperty=nameWithType>, <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType>, ve <xref:System.Windows.Forms.Application.UserAppDataRegistry%2A?displayProperty=nameWithType> özellikleri.|  
  
 Aşağıdaki kod örneği, sürüm ve kültür öznitelikleri bir derlemeye uygulanacak gösterilmektedir.  
  
 [!code-cpp[AssemblyDelaySignAttribute#3](../../../samples/snippets/cpp/VS_Snippets_CLR/AssemblyDelaySignAttribute/cpp/source2.cpp#3)]
 [!code-csharp[AssemblyDelaySignAttribute#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AssemblyDelaySignAttribute/cs/source2.cs#3)]
 [!code-vb[AssemblyDelaySignAttribute#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AssemblyDelaySignAttribute/vb/source2.vb#3)]  
  
## <a name="informational-attributes"></a>Bilgilendirme özniteliklerini  
 Diğer şirket ya da bir derleme için ürün bilgi sağlamak için bilgilendirme özniteliklerini kullanabilirsiniz. Aşağıdaki tabloda, bir derleme için uygulayabileceğiniz bilgilendirme özniteliklerini açıklar.  
  
|Bilgilendirme özniteliği|Açıklama|  
|-----------------------------|-----------------|  
|<xref:System.Reflection.AssemblyCompanyAttribute>|Şirket adını belirten dize değeri.|  
|<xref:System.Reflection.AssemblyCopyrightAttribute>|Telif hakkı bilgileri belirten değeri dize.|  
|<xref:System.Reflection.AssemblyFileVersionAttribute>|Win32 dosya sürüm numarasını belirten dize değeri. Bu normal olarak derleme sürümü için varsayılan olarak.|  
|<xref:System.Reflection.AssemblyInformationalVersionAttribute>|Dize değeri bir tam ürün sürüm numarası gibi ortak dil çalışma zamanı tarafından kullanılmaz sürüm bilgileri belirtme. **Not:** bu özniteliği bir derlemeye uygulanmışsa, belirtir dize çalışma zamanında kullanılarak elde edilebilir <xref:System.Windows.Forms.Application.ProductVersion%2A?displayProperty=nameWithType> özelliği. Dize tarafından sağlanan yolu ve kayıt defteri anahtarı, aynı zamanda kullanılır <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType> ve <xref:System.Windows.Forms.Application.UserAppDataRegistry%2A?displayProperty=nameWithType> özellikleri.|  
|<xref:System.Reflection.AssemblyProductAttribute>|Ürün bilgileri belirten değeri dize.|  
|<xref:System.Reflection.AssemblyTrademarkAttribute>|Ticari marka bilgileri belirten değeri dize.|  
  
 Bu öznitelikler derlemenin Windows özellikleri sayfasında görünebilen ve kullanarak kılınabilir **/win32res** kendi Win32 kaynak dosyası belirtmek için derleyici seçeneği.  
  
## <a name="assembly-manifest-attributes"></a>Derleme bildirimi öznitelikleri  
 Başlık, açıklama, varsayılan diğer ad ve yapılandırma dahil olmak üzere, bir derleme bildirimi bilgilerini sağlamak için derleme bildirimi özniteliklerini kullanabilirsiniz. Aşağıdaki tabloda, derleme bildirimi öznitelikleri açıklanmaktadır.  
  
|Derleme bildirimi özniteliği|Açıklama|  
|---------------------------------|-----------------|  
|<xref:System.Reflection.AssemblyConfigurationAttribute>|Dize, perakende veya hata ayıklama gibi derleme yapılandırmasını gösteren bir değeri. Çalışma zamanı, bu değeri kullanmaz.|  
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|Başvurulan derlemeler tarafından kullanılacak bir varsayılan diğer adını belirten dize değeri. Bu değer, derlemenin adı (bir GUID değeri gibi) kolay olmadığında kolay bir ad sağlar. Bu değer, tam derleme adının kısa biçimi da kullanılabilir.|  
|<xref:System.Reflection.AssemblyDescriptionAttribute>|Dize değeri doğası ve derleme amacı özetler kısa bir açıklama belirtme.|  
|<xref:System.Reflection.AssemblyTitleAttribute>|Derleme için bir kolay ad belirten dize değeri. Örneğin, comdlg adlı bir derleme Microsoft ortak iletişim kutusu denetimi başlık olabilir.|  
  
## <a name="strong-name-attributes"></a>Tanımlayıcı ad öznitelikleri  
 Bir derleme için bir tanımlayıcı adı için tanımlayıcı ad öznitelikleri kullanabilirsiniz. Aşağıdaki tabloda, tanımlayıcı ad özniteliklerini açıklar.  
  
|Tanımlayıcı ad öznitelikleri|Açıklama|  
|----------------------------|-----------------|  
|<xref:System.Reflection.AssemblyDelaySignAttribute>|Gecikmeli imzalama kullanılmakta olduğunu gösteren Boole değeri.|  
|<xref:System.Reflection.AssemblyKeyFileAttribute>|(Gecikmeli imzalama kullanarak varsa) ortak anahtarı içeren dosyanın veya ortak ve özel anahtarlar adını belirten dize bu öznitelik yapıcısına bir parametre olarak geçirildi. Dosya adı (.exe veya .dll), çıkış dosya yolu göreli bir kaynak dosya yolu olmadığını unutmayın.|  
|<xref:System.Reflection.AssemblyKeyNameAttribute>|Bu öznitelik, oluşturucuya bir parametre olarak geçirilen anahtar çiftini içeren anahtar kapsayıcısı belirtir.|  
  
 Aşağıdaki kod örneği kullanarak bir katı adlı derleme ile ortak anahtar dosyası oluşturmak imzalamayı geciktirme çağrıldığında uygulamak için öznitelikleri gösterir `myKey.snk`.  
  
 [!code-cpp[AssemblyDelaySignAttribute#4](../../../samples/snippets/cpp/VS_Snippets_CLR/AssemblyDelaySignAttribute/cpp/source2.cpp#4)]
 [!code-csharp[AssemblyDelaySignAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AssemblyDelaySignAttribute/cs/source2.cs#4)]
 [!code-vb[AssemblyDelaySignAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AssemblyDelaySignAttribute/vb/source2.vb#4)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
- [Bütünleştirilmiş Kodlar Oluşturma](../../../docs/framework/app-domains/create-assemblies.md)  
- [Bütünleştirilmiş Kodlarla Programlama](../../../docs/framework/app-domains/programming-with-assemblies.md)
