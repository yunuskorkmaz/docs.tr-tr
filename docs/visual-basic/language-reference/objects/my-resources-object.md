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
ms.openlocfilehash: 7f5d81194123ad2151a494a3cb79aa1955e0fdad
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350334"
---
# <a name="myresources-object"></a>My.Resources Nesnesi
Uygulamanın kaynaklarına erişmek için özellikler ve sınıflar sağlar.  
  
## <a name="remarks"></a>Açıklamalar  
 `My.Resources` nesnesi, uygulamanın kaynaklarına erişim sağlar ve uygulamanıza yönelik kaynakları dinamik olarak almanızı sağlar. Daha fazla bilgi için bkz. [uygulama kaynaklarını yönetme (.net)](/visualstudio/ide/managing-application-resources-dotnet).  
  
 `My.Resources` nesnesi yalnızca genel kaynakları kullanıma sunar. Formlarla ilişkili kaynak dosyalarına erişim sağlamaz. Form kaynaklarına formdan erişmeniz gerekir.  
  
 Uygulamanın kültüre özgü kaynak dosyalarına `My.Resources` nesnesinden erişebilirsiniz. Varsayılan olarak, `My.Resources` nesnesi kaynak dosyasındaki <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.UICulture%2A> özelliğindeki kültür ile eşleşen kaynakları arar. Ancak, bu davranışı geçersiz kılabilir ve kaynaklar için kullanmak üzere belirli bir kültür belirtebilirsiniz. Daha fazla bilgi için bkz. [Masaüstü uygulamalarındaki kaynaklar](../../../framework/resources/index.md).  
  
## <a name="properties"></a>Özellikler  
 `My.Resources` nesnesinin özellikleri, uygulamanızın kaynaklarına salt okuma erişimi sağlar. Kaynak eklemek veya kaldırmak için, **Proje tasarımcısını**kullanın. `My.Resources.`*resourceName*kullanarak **Proje Tasarımcısı** aracılığıyla eklenen kaynaklara erişebilirsiniz.  
  
 Ayrıca, **Çözüm Gezgini** ' de projenizi seçip **Yeni öğe Ekle ' ye** tıklayarak veya **Proje** menüsünden **Varolan öğe** Ekle ' yi seçerek kaynak dosyalarını ekleyebilir veya kaldırabilirsiniz. `My.Resources.`*resourceFileName*`.`*resourceName*kullanarak bu şekilde eklenen kaynaklara erişebilirsiniz.  
  
 Her kaynağın bir adı, kategorisi ve değeri vardır ve bu kaynak ayarları, kaynağa erişme özelliğinin `My.Resources` nesnesinde nasıl göründüğünü belirlenir. **Proje Tasarımcısı**'nda eklenen kaynaklar için:  
  
- Ad, özelliğin adını belirler,  
  
- Kaynak verileri, özelliğinin değeridir,  
  
- Kategori, özelliğin türünü belirler:  
  
|Kategori|Özellik veri türü|  
|---|---|  
|**Dizeler**|[Dize](../../../visual-basic/language-reference/data-types/string-data-type.md)|  
|**Görüntüler**|<xref:System.Drawing.Bitmap>|  
|**Simgeler**|<xref:System.Drawing.Icon>|  
|**Ses**|<xref:System.IO.UnmanagedMemoryStream><br /><br /> <xref:System.IO.UnmanagedMemoryStream> sınıfı <xref:System.IO.Stream> sınıfından türetilir, bu nedenle <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A> yöntemi gibi akışları alan yöntemlerle kullanılabilir.|  
|**Dosyalar**|metin dosyaları için -   [dizesi](../../../visual-basic/language-reference/data-types/string-data-type.md) .<br />görüntü dosyaları için <xref:System.Drawing.Bitmap> -   .<br />simge dosyaları için <xref:System.Drawing.Icon> -   .<br />ses dosyaları için <xref:System.IO.UnmanagedMemoryStream> -   .|  
|**Diğer**|Tasarımcının **tür** sütunundaki bilgiler tarafından belirlenir.|  
  
## <a name="classes"></a>Sınıflar  
 `My.Resources` nesnesi, her kaynak dosyasını paylaşılan özelliklere sahip bir sınıf olarak kullanıma sunar. Sınıf adı, kaynak dosyasının adıyla aynıdır. Önceki bölümde açıklandığı gibi, bir kaynak dosyasındaki kaynaklar sınıfında Özellikler olarak gösterilir.  
  
## <a name="example"></a>Örnek  
 Bu örnek, bir formun başlığını uygulama kaynak dosyasında `Form1Title` adlı dize kaynağına ayarlar. Örneğin çalışması için, uygulamanın kaynak dosyasında `Form1Title` adlı bir dize olması gerekir.  
  
 [!code-vb[VbVbalrMyResources#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#1)]  
  
## <a name="example"></a>Örnek  
 Bu örnek, formun simgesini uygulamanın kaynak dosyasında depolanan `Form1Icon` adlı simgeye ayarlar. Örneğin çalışması için, uygulamanın kaynak dosyasında `Form1Icon` adlı bir simgeye sahip olması gerekir.  
  
 [!code-vb[VbVbalrMyResources#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#2)]  
  
## <a name="example"></a>Örnek  
 Bu örnek, bir formun arka plan görüntüsünü, uygulama kaynak dosyasında bulunan `Form1Background`adlı görüntü kaynağı olarak ayarlar. Bu örneğin çalışması için, uygulamanın kaynak dosyasında `Form1Background` adlı bir görüntü kaynağı olması gerekir.  
  
 [!code-vb[VbVbalrMyResources#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#3)]  
  
## <a name="example"></a>Örnek  
 Bu örnek, uygulamanın kaynak dosyasında `Form1Greeting` adlı bir ses kaynağı olarak depolanan sesi çalar. Örneğin çalışması için, uygulamanın kaynak dosyasında `Form1Greeting` adlı bir ses kaynağına sahip olması gerekir. `My.Computer.Audio.Play` yöntemi yalnızca Windows Forms uygulamalar için kullanılabilir.  
  
 [!code-vb[VbVbalrMyResources#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#4)]  
  
## <a name="example"></a>Örnek  
 Bu örnekte, uygulamanın dize kaynağının Fransızca-kültür sürümü alınır. Kaynak `Message`olarak adlandırılır. `My.Resources` nesnesinin kullandığı kültürü değiştirmek için, örnek <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.ChangeUICulture%2A>kullanır.  
  
 Bu örneğin çalışması için, uygulamanın kaynak dosyasında `Message` adlı bir dizeye sahip olması ve uygulamanın bu kaynak dosyasının (Resources.fr-FR. resx) Fransızca-kültür sürümüne sahip olması gerekir. Uygulama, kaynak dosyasının Fransızca-kültür sürümüne sahip değilse, `My.Resource` nesnesi kaynağı varsayılan kültür kaynak dosyasından alır.  
  
 [!code-vb[VbVbalrMyResources#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#10)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama Kaynaklarını Yönetme (.NET)](/visualstudio/ide/managing-application-resources-dotnet)
- [Masaüstü Uygulamalarındaki Kaynaklar](../../../framework/resources/index.md)
