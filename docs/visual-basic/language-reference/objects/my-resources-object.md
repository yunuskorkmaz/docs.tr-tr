---
title: My.Resources Nesnesi
ms.date: 07/20/2015
f1_keywords:
- My.Resources
- My.Resources.MyResources.ResourceManager
- My.Resources.MyResources.Culture
helpviewer_keywords:
- My.Resources object
ms.assetid: 34c3f2dc-7b87-432c-9d5f-17ea666bb266
ms.openlocfilehash: 2b7c82c31d2e31ccbf573cf1dfa138af2d99ce29
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84372471"
---
# <a name="myresources-object"></a>My.Resources Nesnesi
Uygulamanın kaynaklarına erişmek için özellikler ve sınıflar sağlar.  
  
## <a name="remarks"></a>Açıklamalar  
 `My.Resources`Nesnesi, uygulamanın kaynaklarına erişim sağlar ve uygulamanıza yönelik kaynakları dinamik olarak almanızı sağlar. Daha fazla bilgi için bkz. [uygulama kaynaklarını yönetme (.net)](/visualstudio/ide/managing-application-resources-dotnet).  
  
 `My.Resources`Nesne yalnızca genel kaynakları kullanıma sunar. Formlarla ilişkili kaynak dosyalarına erişim sağlamaz. Form kaynaklarına formdan erişmeniz gerekir.  
  
 Uygulamanın kültüre özgü kaynak dosyalarına `My.Resources` nesnesinden erişebilirsiniz. Varsayılan olarak, `My.Resources` nesnesi kaynak dosyasındaki, özelliğindeki kültür ile eşleşen kaynakları arar <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.UICulture%2A> . Ancak, bu davranışı geçersiz kılabilir ve kaynaklar için kullanmak üzere belirli bir kültür belirtebilirsiniz. Daha fazla bilgi için bkz. [Masaüstü uygulamalarındaki kaynaklar](../../../framework/resources/index.md).  
  
## <a name="properties"></a>Özellikler  
 Nesnesinin özellikleri, `My.Resources` uygulamanızın kaynaklarına salt okuma erişimi sağlar. Kaynak eklemek veya kaldırmak için, **Proje tasarımcısını**kullanın. ResourceName kullanarak **Proje Tasarımcısı** aracılığıyla eklenen kaynaklara erişebilirsiniz `My.Resources.` *resourceName*.  
  
 Ayrıca, **Çözüm Gezgini** ' de projenizi seçip **Yeni öğe Ekle ' ye** tıklayarak veya **Proje** menüsünden **Varolan öğe** Ekle ' yi seçerek kaynak dosyalarını ekleyebilir veya kaldırabilirsiniz. `My.Resources.` *ResourceFileName* `.` *resourceName*kullanarak bu şekilde eklenen kaynaklara erişebilirsiniz.  
  
 Her kaynağın bir adı, kategorisi ve değeri vardır ve bu kaynak ayarları, kaynağa erişme özelliğinin nesnede nasıl göründüğünü belirlenir `My.Resources` . **Proje Tasarımcısı**'nda eklenen kaynaklar için:  
  
- Ad, özelliğin adını belirler,  
  
- Kaynak verileri, özelliğinin değeridir,  
  
- Kategori, özelliğin türünü belirler:  
  
|Kategori|Özellik veri türü|  
|---|---|  
|**Dizeler**|[Dize](../data-types/string-data-type.md)|  
|**Görüntüler**|<xref:System.Drawing.Bitmap>|  
|**Simgeler**|<xref:System.Drawing.Icon>|  
|**Ses**|<xref:System.IO.UnmanagedMemoryStream><br /><br /> <xref:System.IO.UnmanagedMemoryStream>Sınıfı sınıfından türetilir, bu <xref:System.IO.Stream> nedenle, yöntemi gibi akışlar alan yöntemlerle kullanılabilir <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A> .|  
|**Dosyalar**|-   Metin dosyaları için [dize](../data-types/string-data-type.md) .<br />-   <xref:System.Drawing.Bitmap>görüntü dosyaları için.<br />-   <xref:System.Drawing.Icon>simge dosyaları için.<br />-   <xref:System.IO.UnmanagedMemoryStream>ses dosyaları için.|  
|**Diğer**|Tasarımcının **tür** sütunundaki bilgiler tarafından belirlenir.|  
  
## <a name="classes"></a>Sınıflar  
 `My.Resources`Nesnesi, her kaynak dosyasını paylaşılan özelliklere sahip bir sınıf olarak kullanıma sunar. Sınıf adı, kaynak dosyasının adıyla aynıdır. Önceki bölümde açıklandığı gibi, bir kaynak dosyasındaki kaynaklar sınıfında Özellikler olarak gösterilir.  
  
## <a name="example"></a>Örnek  
 Bu örnek, bir formun başlığını uygulama kaynak dosyasında adlı dize kaynağına ayarlar `Form1Title` . Örneğin çalışması için, uygulamanın kaynak dosyasında adlı bir dize olması gerekir `Form1Title` .  
  
 [!code-vb[VbVbalrMyResources#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#1)]  
  
## <a name="example"></a>Örnek  
 Bu örnek, formun simgesini `Form1Icon` uygulamanın kaynak dosyasında saklanan adlı simgeye ayarlar. Örneğin çalışması için, uygulamanın kaynak dosyasında adında bir simge olması gerekir `Form1Icon` .  
  
 [!code-vb[VbVbalrMyResources#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#2)]  
  
## <a name="example"></a>Örnek  
 Bu örnek, bir formun arka plan görüntüsünü, `Form1Background` uygulama kaynak dosyasında olan adlı görüntü kaynağı olarak ayarlar. Bu örneğin çalışması için, uygulamanın kaynak dosyasında adlı bir görüntü kaynağı olması gerekir `Form1Background` .  
  
 [!code-vb[VbVbalrMyResources#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#3)]  
  
## <a name="example"></a>Örnek  
 Bu örnek `Form1Greeting` , uygulamanın kaynak dosyasında adlı bir ses kaynağı olarak depolanan sesi çalar. Örneğin çalışması için, uygulamanın kaynak dosyasında adlı bir ses kaynağı olmalıdır `Form1Greeting` . `My.Computer.Audio.Play`Yöntemi yalnızca Windows Forms uygulamalar için kullanılabilir.  
  
 [!code-vb[VbVbalrMyResources#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#4)]  
  
## <a name="example"></a>Örnek  
 Bu örnekte, uygulamanın dize kaynağının Fransızca-kültür sürümü alınır. Kaynak adı `Message` . Nesnenin kullandığı kültürü değiştirmek için `My.Resources` , örnek kullanılır <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.ChangeUICulture%2A> .  
  
 Bu örneğin çalışması için, uygulamanın kaynak dosyasında adında bir dize olması `Message` ve uygulamanın, Resources.fr-fr. resx kaynak dosyasının Fransızca-kültür sürümüne sahip olması gerekir. Uygulamanın, kaynak dosyasının Fransızca-kültür sürümü yoksa, `My.Resource` nesne kaynağı varsayılan kültür kaynak dosyasından alır.  
  
 [!code-vb[VbVbalrMyResources#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#10)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama Kaynaklarını Yönetme (.NET)](/visualstudio/ide/managing-application-resources-dotnet)
- [Masaüstü uygulamalarındaki kaynaklar](../../../framework/resources/index.md)
