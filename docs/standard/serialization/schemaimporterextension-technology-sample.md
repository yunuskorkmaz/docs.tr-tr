---
title: SchemaImporterExtension teknoloji örneği
ms.date: 03/30/2017
ms.assetid: 3f5eb78f-0ef6-433a-b095-3a63b1ce0bc9
ms.openlocfilehash: 04e2b3f9fb1ea6f9bbb3c1e1886911cbacda7a62
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54633908"
---
# <a name="schemaimporterextension-technology-sample"></a><span data-ttu-id="21b52-102">SchemaImporterExtension teknoloji örneği</span><span class="sxs-lookup"><span data-stu-id="21b52-102">SchemaImporterExtension Technology Sample</span></span>
[<span data-ttu-id="21b52-103">Örneği indirin</span><span class="sxs-lookup"><span data-stu-id="21b52-103">Download Sample</span></span>](https://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Xml%20Serialization/SchemaImporterExtension.zip.exe)  
  
 <span data-ttu-id="21b52-104">Bu örnek özel bir gösterir <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension> bir XML Şeması alınırken zaman kod oluşturma üzerinde ayrıntılı denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="21b52-104">This sample demonstrates a custom <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension> that allows fine control over code generation when an XML schema is imported.</span></span> <span data-ttu-id="21b52-105">Uygulama oluşturmak, kaydedin ve bu uzantı çağırmak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="21b52-105">The application shows how to build, register and invoke this extension.</span></span>  
  
### <a name="to-build-the-sample-using-the-command-prompt"></a><span data-ttu-id="21b52-106">Komut istemi kullanarak örneği oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="21b52-106">To build the sample using the command prompt</span></span>  
  
1.  <span data-ttu-id="21b52-107">Bir komut istemi penceresi açın ve örnek için dile özgü alt birine gidin.</span><span class="sxs-lookup"><span data-stu-id="21b52-107">Open a Command Prompt window and navigate to one of the language-specific subdirectories for the sample.</span></span>  
  
2.  <span data-ttu-id="21b52-108">Tür **msbuild.exe Orderschemaımporterextension.sln** komut satırına.</span><span class="sxs-lookup"><span data-stu-id="21b52-108">Type **msbuild.exe OrderSchemaImporterExtension.sln** at the command line.</span></span>  
  
### <a name="to-build-the-sample-using-visual-studio"></a><span data-ttu-id="21b52-109">Visual Studio kullanarak örneği oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="21b52-109">To build the sample using Visual Studio</span></span>  
  
1.  <span data-ttu-id="21b52-110">Açık [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] ve örnek için dile özgü alt birine gidin.</span><span class="sxs-lookup"><span data-stu-id="21b52-110">Open [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] and navigate to one of the language-specific subdirectories for the sample.</span></span>  
  
2.  <span data-ttu-id="21b52-111">Visual Studio'da dosyayı açmak OrderSchemaImporterExtension.sln simgesini çift tıklatın.</span><span class="sxs-lookup"><span data-stu-id="21b52-111">Double-click the icon for OrderSchemaImporterExtension.sln to open the file in Visual Studio.</span></span>  
  
3.  <span data-ttu-id="21b52-112">Üzerinde **derleme** menüsünde tıklatın **Çözümü Derle**.</span><span class="sxs-lookup"><span data-stu-id="21b52-112">On the **Build** menu, click **Build Solution**.</span></span>  
  
 <span data-ttu-id="21b52-113">Uygulamayı varsayılan \bin veya \bin\debug'dır dizininde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="21b52-113">The application will be built in the default \bin or \bin\Debug directory.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="21b52-114">Örnek çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="21b52-114">To run the sample</span></span>  
  
1.  <span data-ttu-id="21b52-115">Komut istemi kullanarak yeni yürütülebilir dosyayı içeren dizine gidin.</span><span class="sxs-lookup"><span data-stu-id="21b52-115">Navigate to the directory containing the new executable, using the command prompt.</span></span>  
  
2.  <span data-ttu-id="21b52-116">Tür **[exe adı]** komut satırına.</span><span class="sxs-lookup"><span data-stu-id="21b52-116">Type **[exe name]** at the command line.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="21b52-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="21b52-117">Remarks</span></span>  
 <span data-ttu-id="21b52-118">Örnek ikili oluşturma ve kayıt adımları hakkında daha fazla bilgi için kaynak kodu ve build.proj dosyalarındaki açıklamaları bakın.</span><span class="sxs-lookup"><span data-stu-id="21b52-118">For more information about sample binary creation and registration steps, see the comments in the source code and build.proj files.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21b52-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="21b52-119">See also</span></span>

- <xref:System.CodeDom.CodeCompileUnit>
- <xref:System.CodeDom.CodeNamespace>
- <xref:System.CodeDom.CodeNamespaceImport>
- <xref:Microsoft.CSharp.CSharpCodeProvider>
- <xref:System.Xml.Serialization.IXmlSerializable>
- <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension>
- <xref:System.CodeDom>
- <xref:System.CodeDom.Compiler>
- <xref:System.Web.Services.Description>
- <xref:System.Web.Services.Discovery>
- <xref:System.Xml.Serialization>
- <xref:System.Uri>
- <xref:Microsoft.VisualBasic.VBCodeProvider>
- <xref:System.Web.Services.Description.WebReference>
- <xref:System.Xml.Serialization.XmlSchemaImporter>
