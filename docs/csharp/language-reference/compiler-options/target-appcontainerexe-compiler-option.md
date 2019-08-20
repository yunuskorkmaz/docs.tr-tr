---
title: '-target: appcontainerexe (C# derleyici seçenekleri)'
ms.date: 07/20/2015
ms.assetid: e7e62229-23ea-4e53-bef5-380d951bf95f
ms.openlocfilehash: 09ae01d95138b72a0012f294189d288fc71c74b2
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606539"
---
# <a name="-targetappcontainerexe-c-compiler-options"></a><span data-ttu-id="08f5b-102">-target: appcontainerexe (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="08f5b-102">-target:appcontainerexe (C# Compiler Options)</span></span>
<span data-ttu-id="08f5b-103">**-Target: appcontainerexe** derleyici seçeneğini kullanırsanız, derleyici bir uygulama kapsayıcısında çalıştırılması gereken bir Windows çalıştırılabilir (. exe) dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="08f5b-103">If you use the **-target:appcontainerexe** compiler option, the compiler creates a Windows executable (.exe) file that must be run in an app container.</span></span> <span data-ttu-id="08f5b-104">Bu seçenek [-target: winexe](./target-winexe-compiler-option.md) ile eşdeğerdir, ancak uygulamalar için [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="08f5b-104">This option is equivalent to [-target:winexe](./target-winexe-compiler-option.md) but is designed for [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] apps.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08f5b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="08f5b-105">Syntax</span></span>  
  
```console  
-target:appcontainerexe  
```  
  
## <a name="remarks"></a><span data-ttu-id="08f5b-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="08f5b-106">Remarks</span></span>  
 <span data-ttu-id="08f5b-107">Uygulamanın bir uygulama kapsayıcısında çalışmasını gerektirmek için, bu seçenek [taşınabilir yürütülebilir](/windows/desktop/Debug/pe-format) (PE) dosyasında bir bit ayarlar.</span><span class="sxs-lookup"><span data-stu-id="08f5b-107">To require the app to run in an app container, this option sets a bit in the [Portable Executable](/windows/desktop/Debug/pe-format) (PE) file.</span></span> <span data-ttu-id="08f5b-108">Bu bit ayarlandığında, CreateProcess yöntemi bir uygulama kapsayıcısının dışında yürütülebilir dosyayı başlatmaya çalışırsa bir hata oluşur.</span><span class="sxs-lookup"><span data-stu-id="08f5b-108">When that bit is set, an error occurs if the CreateProcess method tries to launch the executable file outside an app container.</span></span>  
  
 <span data-ttu-id="08f5b-109">[-Out](./out-compiler-option.md) seçeneğini kullanmadığınız takdirde, çıkış dosyası adı [Main](../../programming-guide/main-and-command-args/index.md) metodunu içeren giriş dosyasının adını alır.</span><span class="sxs-lookup"><span data-stu-id="08f5b-109">Unless you use the [-out](./out-compiler-option.md) option, the output file name takes the name of the input file that contains the [Main](../../programming-guide/main-and-command-args/index.md) method.</span></span>  
  
 <span data-ttu-id="08f5b-110">Bu seçeneği bir komut isteminde belirttiğinizde, yürütülebilir dosyayı oluşturmak için bir sonraki **dışarı** veya **-hedef** seçeneğine kadar tüm dosyalar kullanılır.</span><span class="sxs-lookup"><span data-stu-id="08f5b-110">When you specify this option at a command prompt, all files until the next **-out** or **-target** option are used to create the executable file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-ide"></a><span data-ttu-id="08f5b-111">Bu derleyici seçeneğini IDE içinde ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="08f5b-111">To set this compiler option in the IDE</span></span>  
  
1. <span data-ttu-id="08f5b-112">**Çözüm Gezgini**' de, projeniz için kısayol menüsünü açın ve ardından **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="08f5b-112">In **Solution Explorer**, open the shortcut menu for your project, and then choose **Properties**.</span></span>  
  
2. <span data-ttu-id="08f5b-113">**Uygulama** sekmesinde, **Çıkış türü** listesinde, **Windows Mağazası uygulaması**' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="08f5b-113">On the **Application** tab, in the **Output type** list, choose **Windows Store App**.</span></span>  
  
     <span data-ttu-id="08f5b-114">Bu seçenek yalnızca uygulama şablonları için [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="08f5b-114">This option is available only for [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] app templates.</span></span>  
  
 <span data-ttu-id="08f5b-115">Bu derleyici seçeneğini program aracılığıyla ayarlama hakkında daha fazla bilgi için bkz <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="08f5b-115">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="08f5b-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="08f5b-116">Example</span></span>  
 <span data-ttu-id="08f5b-117">Aşağıdaki komut, yalnızca `filename.cs` bir uygulama kapsayıcısında çalıştırılabilen bir Windows yürütülebilir dosyası için derlenir.</span><span class="sxs-lookup"><span data-stu-id="08f5b-117">The following command compiles `filename.cs` into a Windows executable file that can be run only in an app container.</span></span>  
  
```console  
csc -target:appcontainerexe filename.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="08f5b-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="08f5b-118">See also</span></span>

- [<span data-ttu-id="08f5b-119">-target (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="08f5b-119">-target (C# Compiler Options)</span></span>](./target-compiler-option.md)
- [<span data-ttu-id="08f5b-120">-target: winexe (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="08f5b-120">-target:winexe (C# Compiler Options)</span></span>](./target-winexe-compiler-option.md)
- [<span data-ttu-id="08f5b-121">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="08f5b-121">C# Compiler Options</span></span>](./index.md)
